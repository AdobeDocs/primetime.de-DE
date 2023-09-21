---
description: Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.
title: Schnelles Vorwärts- und Rückspulen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Übersicht {#implement-fast-forward-and-rewind-overview}

Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 festlegen.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert festlegen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Wiedergabemodus, indem Sie die Rate auf der `MediaPlayer` auf einen zulässigen Wert.

   * Die `MediaPlayerItem` -Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

   In diesem Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate gesetzt.

   ```java
   import com.adobe.mediacore.MediaPlayer; 
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerException; 
   import java.util.List; 
   import java.lang.Float; 
   
   private boolean setPlaybackRate(MediaPlayer player, float rate) throws MediaPlayerException  
   { 
       //Get list of playback rates that the media player supports 
       MediaPlayerItem item = player.getCurrentItem(); 
       if(item == null) return false; 
       List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
   
       //Return false if requested rate is not supported 
       if(availableRates.indexOf(rate) == -1) return false; 
   
       //Otherwise set the playback rate to the requested rate  
       //(this can throw MediaPlayerException) 
       player.setRate(rate); 
       return true; 
   }
   ```

1. Optional können Sie auf Ratenänderungs-Ereignisse warten, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann eine Ratenänderung tatsächlich stattfindet.

       TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trick Play-Methode:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wenn die `rate` ändert sich in einen anderen Wert.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

     TVSDK sendet beide Ereignisse, wenn der Player aus dem Trick-Play-Modus in den normalen Wiedergabemodus zurückkehrt.
