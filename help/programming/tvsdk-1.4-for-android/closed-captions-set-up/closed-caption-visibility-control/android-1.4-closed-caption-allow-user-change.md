---
description: Dies ist ein Beispiel dafür, wie eine Schaltfläche erstellt wird, mit der ein Benutzer eine Untertitelspur auswählen kann.
title: 'Beispiel: Benutzern erlauben, die Beschriftungsspur zu ändern'
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Beispiel: Benutzer können die Beschriftungsspur ändern{#example-allow-users-to-change-the-caption-track}

Dies ist ein Beispiel dafür, wie eine Schaltfläche erstellt wird, mit der ein Benutzer eine Untertitelspur auswählen kann.

1. Erstellen Sie eine einfache Schaltfläche, um den Track der Untertitel zu ändern.

   ```xml
      <Button 
     android:id="@+id/selectCC" 
     android:layout_width="wrap_content" 
     android:layout_height="wrap_content" 
     android:layout_alignParentBottom="true" 
     android:layout_alignParentRight="true" 
     android:layout_marginRight="10dp" 
     android:onClick="selectClosedCaptioningClick" 
     android:text="CC" /> 
   ```

1. Konvertieren Sie die Liste der verfügbaren Untertitelspuren in ein Zeichenfolgen-Array. Die von TVSDK erkannten Untertitelspuren mit Aktivitäten, d. h. Kanäle, für die TVSDK Daten gefunden hat, werden entsprechend markiert:

   ```java
   /** 
   * Converts the closed captions tracks to a string array. 
   * 
   * @return array of CC tracks 
   */ 
   private String[] getCCsAsArray() { 
       List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); 
       MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
       if (currentItem != null) { 
           List<ClosedCaptionsTrack> closedCaptionsTracks = 
             currentItem.getClosedCaptionsTracks(); 
           Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator(); 
           while (iterator.hasNext()) { 
               ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); 
               String isActive = closedCaptionsTrack.isActive() ? " (" + getString(R.string.active)+ ")" : ""; 
               closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName() + isActive); 
           } 
       } 
       return closedCaptionsTracksAsStrings.toArray(new 
       String[closedCaptionsTracksAsStrings.size()]); 
   } 
   ```

1. Wenn der Benutzer auf die Schaltfläche klickt, zeigen Sie ein Dialogfeld an, in dem alle standardmäßigen CC-Tracks aufgeführt sind.

   ```java
      public void selectClosedCaptioningClick(View view) { 
       Log.i(LOG_TAG + "#selectClosedCaptions", "Displaying closed captions chooser dialog."); 
       final String items[] = getCCsAsArray(); 
       final AlertDialog.Builder ab = new AlertDialog.Builder(this); 
       ab.setTitle(R.string.PlayerControlCCDialogTitle); 
       ab.setSingleChoiceItems(items, selectedClosedCaptionsIndex, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
               // Select the new closed captioning track. 
               MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
               ClosedCaptionsTrack desiredClosedCaptionsTrack = currentItem.getClosedCaptionsTracks().get(whichButton); 
               boolean result = currentItem.selectClosedCaptionsTrack(desiredClosedCaptionsTrack); 
               if (result) { 
                   selectedClosedCaptionsIndex = whichButton; 
               } 
               // Dismiss dialog. 
               dialog.cancel(); 
           } 
       }).setNegativeButton(R.string.PlayerControlCCDialogCancel, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
           // Just cancel the dialog. 
           } 
       }); 
       ab.show(); 
   } 
   ```
