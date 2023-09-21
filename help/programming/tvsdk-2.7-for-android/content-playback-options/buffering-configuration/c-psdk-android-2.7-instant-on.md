---
description: Die Aktivierung von Instant on bedeutet, dass mindestens ein Kanal vorab geladen wird. Wenn Benutzer einen Kanal auswählen oder Kanäle wechseln, wird der Inhalt sofort wiedergegeben. Die Pufferung ist abgeschlossen, wenn der Benutzer mit der Wiedergabe beginnt.
title: Sofort aktiviert
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Sofort aktiviert {#instant-on}

Die Aktivierung von Instant on bedeutet, dass mindestens ein Kanal vorab geladen wird. Wenn Benutzer einen Kanal auswählen oder Kanäle wechseln, wird der Inhalt sofort wiedergegeben. Die Pufferung ist abgeschlossen, wenn der Benutzer mit der Wiedergabe beginnt.

Ohne Instant On initialisiert TVSDK die abzuspielenden Medien, startet jedoch nicht die Pufferung des Streams, bis die Anwendung aufruft `play`. Der Benutzer sieht keinen Inhalt, bis die Pufferung abgeschlossen ist. Mit Instant On können Sie mehrere Instanzen des Medienplayers (oder des Medienplayer-Element-Laders) starten, und TVSDK startet sofort die Pufferung der Streams. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird `play` im neuen Kanal wird die Wiedergabe sofort gestartet.

Die Anzahl der `MediaPlayer` und `MediaPlayerItemLoader` -Instanzen, die TVSDK ausführen kann, wodurch mehr Instanzen ausgeführt werden, mehr Ressourcen verbrauchen. Die Anwendungsleistung kann durch die Anzahl der ausgeführten Instanzen beeinflusst werden. Weitere Informationen finden Sie unter `MediaPlayerItemLoader`, siehe [Laden einer Medienressource im Medienplayer](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK unterstützt keine einzelne `QoSProvider` für beide `itemLoader` und `MediaPlayer`. Wenn der Kunde Instant On verwendet, muss die Anwendung zwei QoS-Instanzen verwalten und beide Instanzen für die Informationen verwalten.

Weitere Informationen finden Sie unter `MediaPlayerItemLoader`, siehe [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

## Hinzufügen einer QoS-Provider-Instanz zu mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Erstellen und Anfügen eines QoS-Anbieters an einen `mediaPlayerItemLoader` instance

  ```
  // Create an instance of QoSProvider  
  private QOSProvider _qosProvider = new QOSProvider(this._context);  
  
  // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
  // (before calling load API on mediaPlayerItemLoader instance)  
  _qosProvider.attachMediaPlayerItemLoader(this._loader); 
  ```

  Sobald die Wiedergabe beginnt, verwenden Sie die `_qosProvider` um `timeToLoad` und `timeToPrepare` QoSdata Die verbleibenden QoS-Metriken können mit der `QoSProvider` an die `mediaPlayer`.

  Weitere Informationen finden Sie unter `MediaPlayerItemLoader`, siehe [Laden einer Medienressource mit MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md#use-mediaplayeritemloader).

## Pufferung für Sofortiges Aktivieren konfigurieren {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK bietet Methoden und Status, mit denen Sie Instant On mit einer Medienressource verwenden können.

>[!NOTE]
>
>Adobe empfiehlt, `MediaPlayerItemLoader` für InstantOn. Verwendung `MediaPlayerItemLoader`, anstatt `MediaPlayer`, siehe media-resource-load-using-mediaplayeritemloader .

1. Vergewissern Sie sich, dass die Ressource geladen wurde und der Player bereit ist, die Ressource wiederzugeben.
1. Vor dem Aufruf `play`, Aufruf `prepareBuffer` für jeden `MediaPlayer` -Instanz.

   >[!NOTE]
   >
   >`prepareBuffer` aktiviert Instant On und TVSDK startet die Pufferung sofort und sendet die `BUFFERING_COMPLETED` -Ereignis, wenn der Puffer voll ist.

   >[!TIP]
   >
   >Standardmäßig ist `prepareBuffer` und `prepareToPlay` Richten Sie den Medien-Stream so ein, dass die Wiedergabe von Anfang an beginnt. Um an einer anderen Position zu beginnen, übergeben Sie die Position (in Millisekunden) an `prepareToPlay`.

   ```
   @Override 
   public void onStatusChanged(MediaPlayerStatus status) { 
       switch (status) { 
           case INITIALIZED: 
               // This example starts 5 seconds into the stream. 
               mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Wenn Sie die `BUFFERING_COMPLETE` -Ereignis, starten Sie die Wiedergabe des Elements oder zeigen Sie visuelles Feedback an, um anzuzeigen, dass der Inhalt vollständig gepuffert ist.

   >[!NOTE]
   >
   >Wenn Sie `play`, sollte die Wiedergabe sofort beginnen.
