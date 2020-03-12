---
description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.
seo-description: Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.
seo-title: Schnelles Vorwärts- und Zurückspulen implementieren
title: Schnelles Vorwärts- und Zurückspulen implementieren
uuid: 2e5d0fd0-0290-4f08-b9c6-c8ecde26abb8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Übersicht {#implement-fast-forward-and-rewind-overview}

Wenn Benutzer die Medien schnell vorwärts oder schnell zurückspulen, befinden sie sich im Trick Play-Modus. Um in den Trick Play-Modus zu wechseln, müssen Sie die MediaPlayer-Wiedergaberate auf einen anderen Wert als 1 einstellen.

Um die Geschwindigkeit zu wechseln, müssen Sie einen Wert einstellen.

1. Wechseln Sie vom normalen Wiedergabemodus (1x) zum Trick-play-Modus, indem Sie die Rate auf einen erlaubten `MediaPlayer` Wert einstellen.

   * Die `MediaPlayerItem` Klasse definiert die zulässigen Wiedergaberaten.
   * TVSDK wählt die nächstzulässige Rate aus, wenn die angegebene Rate nicht zulässig ist.
   In diesem Beispiel wird die interne Wiedergaberate des Players auf die angeforderte Rate eingestellt.

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

1. Sie können optional auf Ratenänderungen-Ereignis hören, die Sie darüber informieren, wann Sie eine Ratenänderung angefordert haben und wann eine Ratenänderung tatsächlich stattfindet.

       TVSDK sendet die folgenden Ereignisse im Zusammenhang mit der Trickwiedergabe:
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` wenn sich der `rate` Wert in einen anderen Wert ändert.

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` wenn die Wiedergabe mit der ausgewählten Rate fortgesetzt wird.

      TVSDK löst beide Ereignis aus, wenn der Player vom Trick-Play-Modus zum normalen Wiedergabemodus zurückkehrt.

