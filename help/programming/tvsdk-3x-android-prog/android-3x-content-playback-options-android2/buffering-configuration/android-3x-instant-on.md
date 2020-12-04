---
description: Durch Aktivieren von "Sofort ein"werden ein oder mehrere Kanal vorgeladen. Wenn Benutzer einen Kanal auswählen oder den Kanal wechseln, wird der Inhalt sofort abgespielt. Die Pufferung ist abgeschlossen, wenn der Benutzer die Anzeige Beginn.
seo-description: Durch Aktivieren von "Sofort ein"werden ein oder mehrere Kanal vorgeladen. Wenn Benutzer einen Kanal auswählen oder den Kanal wechseln, wird der Inhalt sofort abgespielt. Die Pufferung ist abgeschlossen, wenn der Benutzer die Anzeige Beginn.
seo-title: Sofort ein
title: Sofort ein
uuid: 5b1ceace-cae7-44c7-b4b9-d45078d58cc3
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Sofort bei {#instant-on}

Durch Aktivieren von &quot;Sofort ein&quot;werden ein oder mehrere Kanal vorgeladen. Wenn Benutzer einen Kanal auswählen oder den Kanal wechseln, wird der Inhalt sofort abgespielt. Die Pufferung ist abgeschlossen, wenn der Benutzer die Anzeige Beginn.

Ohne Instant On initialisiert TVSDK die wiederzugebenden Medien, puffert den Stream jedoch nicht, bis die Anwendung `play` aufruft. Dem Benutzer werden erst dann Inhalte angezeigt, wenn die Pufferung abgeschlossen ist. Mit &quot;Sofort ein&quot;können Sie mehrere Instanzen des Medienplayers (oder des Medienplayer-Elementladers) starten, und TVSDK-Beginn können die Streams sofort zwischenspeichern. Wenn ein Benutzer den Kanal ändert und der Stream ordnungsgemäß gepuffert wurde, wird `play` auf den neuen Kanal-Beginn sofort wiedergegeben.

Auch wenn die Anzahl der TVSDK-Instanzen `MediaPlayer` und `MediaPlayerItemLoader` nicht begrenzt ist, verbraucht das Ausführen von mehr Instanzen mehr Ressourcen. Die Anwendungsleistung kann durch die Anzahl der ausgeführten Instanzen beeinträchtigt werden. Weitere Informationen zu `MediaPlayerItemLoader` finden Sie unter [Medienressource im Medienplayer](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md) laden.

>[!IMPORTANT]
>
>TVSDK unterstützt kein einzelnes `QoSProvider`, um sowohl mit `itemLoader` als auch mit `MediaPlayer` zu arbeiten. Wenn der Kunde Instant On verwendet, muss die Anwendung zwei QoS-Instanzen verwalten und beide Instanzen für die Informationen verwalten.

Weitere Informationen zu `MediaPlayerItemLoader` finden Sie unter [Medienressource mit MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md) laden.

## hinzufügen einer QoS-Provider-Instanz zu mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Einen QoS-Provider erstellen und an eine `mediaPlayerItemLoader`-Instanz anhängen

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Verwenden Sie nach den Beginn für die Wiedergabe `_qosProvider`, um `timeToLoad` und `timeToPrepare` QoSdata abzurufen. Die verbleibenden QoS-Metriken können mithilfe der `QoSProvider`, die mit `mediaPlayer` verbunden sind, abgerufen werden.

   Weitere Informationen zu `MediaPlayerItemLoader` finden Sie unter [Medienressource mit MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md) laden.

## Pufferung für Instant on konfigurieren{#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK stellt Methoden und Status bereit, mit denen Sie Instant On mit einer Medienressource verwenden können.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung von `MediaPlayerItemLoader` für InstantOn. Informationen zum Verwenden von `MediaPlayerItemLoader` anstelle von `MediaPlayer` finden Sie unter [Medienressource mit MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md) laden.

1. Vergewissern Sie sich, dass die Ressource geladen wurde und der Player bereit ist, die Ressource wiederzugeben.
1. Rufen Sie vor dem Aufruf von `play` für jede `MediaPlayer`-Instanz `prepareBuffer` auf.

   `prepareBuffer` aktiviert Instant On- und TVSDK-Beginn sofort Pufferung und löst das  `BUFFERING_COMPLETED` Ereignis aus, wenn der Puffer voll ist.

   >[!TIP]
   >
   >Standardmäßig richten `prepareBuffer` und `prepareToPlay` den Medienstream auf Beginn ein, der von Anfang an abgespielt wird. Übergeben Sie die Position (in Millisekunden) an `prepareToPlay`, um einen Beginn an einer anderen Position durchzuführen.

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

1. Wenn Sie das `BUFFERING_COMPLETE`-Ereignis erhalten, geben Sie beim Abspielen des Elements oder durch visuelles Feedback an, dass der Inhalt vollständig gepuffert ist.

   >[!NOTE]
   >
   >Wenn Sie `play` aufrufen, sollte die Wiedergabe sofort beginnen.