---
description: Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, legen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 fest.
title: Schnelles Vorwärts- und Rückspulen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Übersicht {#implement-fast-forward-and-rewind}

Wenn Benutzer schnell vorwärts oder schnell durch die Medien zurückkehren, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, legen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 fest.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert festlegen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Wiedergabemodus, indem Sie die Rate auf der `MediaPlayer` auf einen zulässigen Wert.

       Beachten Sie die folgenden Informationen:
   
   * Die `MediaPlayerItem` -Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

     Im folgenden Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate gesetzt:

     ```
     import com.adobe.mediacore.MediaPlayer; 
     import com.adobe.mediacore.MediaPlayerItem; 
     import com.adobe.mediacore.MediaPlayerException; 
     import java.util.List; 
     import java.lang.Float; 
     
     private boolean setPlaybackRate(MediaPlayer player, float rate)  
       throws MediaPlayerException { 
         // Get list of playback rates that the media player supports 
         MediaPlayerItem item = player.getCurrentItem(); 
         if (item == null) return false; 
         List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
     
         // Return false if requested rate is not supported 
         if (availableRates.indexOf(rate) == -1) return false; 
     
         // Otherwise set the playback rate to the requested rate  
         // (this can throw MediaPlayerException) 
         player.setRate(rate); 
         return true; 
     }
     ```

1. Optional können Sie auf Ratenänderungsereignisse warten, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann die Ratenänderung tatsächlich eintritt.

TVSDK versendet die folgenden Ereignisse, die mit der Wiedergabe von Tricks zusammenhängen:

* `MediaPlayerEvent.RATE_SELECTED`, wenn die `rate` ändert sich in einen anderen Wert.

* `MediaPlayerEvent.RATE_PLAYING`, wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

  TVSDK sendet diese Ereignisse, wenn der Player aus dem Trick Play-Modus in den normalen Wiedergabemodus zurückkehrt.
