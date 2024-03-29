---
description: Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der Anzeigenklicks verwaltet. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.
title: Trennen Sie den klickbaren Anzeigenprozess.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Trennen Sie den klickbaren Anzeigenprozess.{#separate-the-clickable-ad-process}

Sie sollten die Logik der Benutzeroberfläche Ihres Players von dem Prozess trennen, der Anzeigenklicks verwaltet. Eine Möglichkeit dazu besteht darin, mehrere Fragmente für eine Aktivität zu implementieren.

1. Implementieren eines Fragments, das die `MediaPlayer` und die für die Videowiedergabe verantwortlich sind.

   Dieses Fragment sollte aufrufen `notifyClick`.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. Implementieren Sie ein anderes Fragment, um ein UI-Element anzuzeigen, das anzeigt, dass auf eine Anzeige geklickt werden kann, dieses UI-Element zu überwachen und Benutzer-Klicks mit dem Fragment zu kommunizieren, das die `MediaPlayer`.

   Dieses Fragment sollte eine Schnittstelle für die Fragmentkommunikation deklarieren. Das Fragment erfasst die Implementierung der Schnittstelle während der onAttach-Lebenszyklusmethode und kann die Oberflächenmethoden aufrufen, um mit der Aktivität zu kommunizieren.

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
