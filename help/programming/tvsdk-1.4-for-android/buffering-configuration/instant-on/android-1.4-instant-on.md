---
description: Der Begriff "Instant on"bezieht sich auf das Vorausfüllen eines oder mehrerer Kanäle, sodass Benutzer, die einen Kanal auswählen oder Kanäle wechseln, sofort Inhalte wiedergeben können. Die Pufferung ist bereits zu dem Zeitpunkt abgeschlossen, zu dem der Benutzer die Wiedergabe startet.
title: Sofort aktiviert
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Sofort aktiviert {#instant-on}

Der Begriff &quot;Instant on&quot;bezieht sich auf das Vorausfüllen eines oder mehrerer Kanäle, sodass Benutzer, die einen Kanal auswählen oder Kanäle wechseln, sofort Inhalte wiedergeben können. Die Pufferung ist bereits zu dem Zeitpunkt abgeschlossen, zu dem der Benutzer die Wiedergabe startet.

TVSDK initialisiert ohne sofortigen Start die abzuspielenden Medien, startet jedoch nicht die Pufferung des Streams, bis die Anwendung aufruft `play`. Der Benutzer sieht keinen Inhalt, bis die Pufferung abgeschlossen ist. Mit sofortiger Wirkung können Sie mehrere Instanzen des Medienplayers (oder des Medienplayer-Element-Laders) starten, und TVSDK startet sofort die Pufferung der Streams.

Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird `play` im neuen Kanal wird die Wiedergabe sofort gestartet.

Die Anzahl der `MediaPlayer` -Instanzen, die TVSDK ausführen kann, wodurch mehr Instanzen ausgeführt werden, mehr Ressourcen verbrauchen. Die Anwendungsleistung kann von der Anzahl der ausgeführten Instanzen beeinflusst werden. Weitere Informationen zu diesen Instanzen finden Sie unter [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Pufferung für sofortige Wiedergabe konfigurieren {#configure-buffering-for-instant-on-playback}

Mit sofortigem Einschalten können Benutzer die Kanäle wechseln und die Wiedergabe wird sofort ohne Wartezeit gestartet. Wenn Sie Sofort aktiviert haben, puffert TVSDK mindestens einen Kanal, bevor die Wiedergabe beginnt.

1. Vergewissern Sie sich, dass die Ressource geladen wurde und wiedergegeben werden kann, indem Sie überprüfen, ob der Status VORBEREITET ist.
1. Vor dem Aufruf `play`, Aufruf `prepareBuffer` für jeden `MediaPlayer` -Instanz.

   Dies ermöglicht den sofortigen Start, was bedeutet, dass TVSDK mit der Pufferung beginnt, ohne die Medienressource tatsächlich wiederzugeben. TVSDK sendet die `BUFFERING_COMPLETED` -Ereignis, wenn der Puffer voll ist.

   >[!NOTE]
   >
   >Standardmäßig ist `prepareBuffer` und `prepareToPlay` Richten Sie den Medien-Stream so ein, dass die Wiedergabe von Anfang an beginnt. Um an einer anderen Position zu beginnen, übergeben Sie die Position (in Millisekunden) an `prepareToPlay`.

   ```java
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state,  
                              MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               // By default, prepareToPlay and prepareBuffer buffer and start playing 
               // from the beginning of the stream. To start at another position, 
               // pass it into prepareToPlay. This example starts 5 seconds into the stream. 
               _mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               _mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Wenn Sie die `BUFFERING_COMPLETE` -Ereignis, starten Sie die Wiedergabe des Elements oder zeigen Sie visuelles Feedback an, um anzuzeigen, dass der Inhalt vollständig gepuffert ist.

   Wenn Sie `play`, sollte die Wiedergabe sofort beginnen.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
