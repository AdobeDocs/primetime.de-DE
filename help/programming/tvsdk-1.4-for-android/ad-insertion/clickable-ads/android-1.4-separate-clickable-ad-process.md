---
description: Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der die Verwaltung von Anzeigenklicks ausführt. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.
seo-description: Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der die Verwaltung von Anzeigenklicks ausführt. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.
seo-title: Trennen des klickbaren Anzeigenprozesses
title: Trennen des klickbaren Anzeigenprozesses
uuid: 00537191-8997-418d-add2-8e86d818c76e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Trennen des klickbaren Anzeigenprozesses{#separate-the-clickable-ad-process}

Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der die Verwaltung von Anzeigenklicks ausführt. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.

1. Implementieren Sie ein Fragment, das die Variable enthält `MediaPlayer` und für die Videowiedergabe verantwortlich ist.

   Dieses Fragment sollte aufgerufen werden `notifyClick`.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. Implementieren Sie ein anderes Fragment, um ein UI-Element anzuzeigen, das anzeigt, dass eine Anzeige anklickbar ist, überwachen Sie dieses UI-Element und teilen Sie dem Fragment, das das Fragment enthält, die Benutzerklicks mit `MediaPlayer`.

   Dieses Fragment sollte eine Schnittstelle für die Fragmentkommunikation deklarieren. Das Fragment erfasst die Implementierung der Schnittstelle während der onAttach-Lebenszyklusmethode und kann die Schnittstellenmethoden aufrufen, um mit der Aktivität zu kommunizieren.

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
   
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container, Bundle 
                                savedInstanceState) { 
   
           // the custom fragment is defined by a custom button 
           viewGroup =  
             (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad, container, false); 
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

