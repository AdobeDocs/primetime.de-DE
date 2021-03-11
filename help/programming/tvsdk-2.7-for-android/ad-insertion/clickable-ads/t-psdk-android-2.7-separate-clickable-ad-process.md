---
description: Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der die Verwaltung von Anzeigenklicks ausführt. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.
title: Trennen des klickbaren Anzeigenprozesses
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Trennen Sie den klickbaren Anzeigenprozess {#separate-the-clickable-ad-process}

Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der die Verwaltung von Anzeigenklicks ausführt. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.

1. Implementieren Sie ein Fragment, um das `MediaPlayer` zu enthalten.

   Dieses Fragment sollte `notifyClick()` aufrufen und ist für die Videowiedergabe verantwortlich.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. Implementieren Sie ein anderes Fragment, um ein UI-Element anzuzeigen, das anzeigt, dass eine Anzeige anklickbar ist, überwachen Sie dieses UI-Element und teilen Sie dem Fragment mit, das das `MediaPlayer` enthält.

   Dieses Fragment sollte eine Schnittstelle für die Fragmentkommunikation deklarieren. Das Fragment erfasst die Implementierung der Schnittstelle während der Lebenszyklusmethode von `onAttach()` und kann die Schnittstellenmethoden aufrufen, um mit der Aktivität zu kommunizieren.

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container,  
                                Bundle savedInstanceState) { 
           // the custom fragment is defined by a custom button 
           viewGroup = (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad,  
                                                    container, false); 
           button = (Button) viewGroup.findViewById(R.id.clickButton); 
   
           // register a click listener to detect user interaction 
           button.setOnClickListener(new View.OnClickListener() { 
               @Override 
               public void onClick(View v) { 
                   // send the event back to the activity 
                   callback.onAdClick(); 
               } 
           }); 
           viewGroup.setVisibility(View.INVISIBLE); 
           return viewGroup; 
       } 
   
       public void hide() { 
           viewGroup.setVisibility(View.INVISIBLE); 
       } 
   
       public void show() { 
           viewGroup.setVisibility(View.VISIBLE);     
       } 
   
       @Override 
       public void onAttach(Activity activity) { 
           super.onAttach(activity); 
           // attaches the interface implementation 
           // if the container activity does not implement the methods  
           // from the interface an exception will be thrown 
           try { 
               callback = (OnAdUserInteraction) activity; 
           } catch (ClassCastException e) { 
               throw new ClassCastException(activity.toString() 
                   + " must implement OnAdUserInteraction"); 
           }     
       } 
   
       // user defined interface that allows fragment communication 
       // must be implemented by the container activity 
       public interface OnAdUserInteraction { 
           public void onAdClick(); 
       } 
   } 
   ```

