---
description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, legen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 fest.
seo-description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, legen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 fest.
seo-title: Schnelles Vorwärts- und Zurückspulen implementieren
title: Schnelles Vorwärts- und Zurückspulen implementieren
uuid: 070a3331-43a3-4517-9cd9-06d817ffcfbd
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Übersicht {#implement-fast-forward-and-rewind-overview}

Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, legen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 fest.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert einstellen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Trick-play-Modus, indem Sie die Rate für das `MediaPlayer` auf einen erlaubten Wert einstellen.

       Beachten Sie die folgenden Informationen:
   
   * Die `MediaPlayerItem`-Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.

      Im folgenden Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate eingestellt:

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

1. Sie können optional auf Ratenänderungs-Ereignis hören, die Sie darüber informieren, wenn Sie eine Ratenänderung angefordert haben und wenn die Ratenänderung tatsächlich eintritt.

       TVSDK sendet die folgenden Ereignis, die sich auf die Trickwiedergabe beziehen:
   
   * `MediaPlayerEvent.RATE_SELECTED`, wenn sich der  `rate` Wert in einen anderen Wert ändert.

   * `MediaPlayerEvent.RATE_PLAYING`, wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

      TVSDK löst diese Ereignis aus, wenn der Player vom Trick Play-Modus zum normalen Play-Modus zurückkehrt.

