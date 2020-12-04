---
description: Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
seo-description: Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
seo-title: Anzeigen bei vollständiger Wiedergabe im Ereignis aktivieren
title: Anzeigen bei vollständiger Wiedergabe im Ereignis aktivieren
uuid: 69244069-ef61-42e4-b2f5-62ae2561d9e1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Anzeigen im Vollbildmodus aktivieren {#enable-ads-in-full-event-replay-overview}

Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/Lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird dem Live-Manifest ein `EXT-X-ENDLIST`-Tag angehängt. Bei HLS bedeutet das `EXT-X-ENDLIST`-Tag, dass der Stream ein VOD-Stream ist. Um Anzeigen korrekt einzufügen, kann TVSDK diesen Stream nicht automatisch von einem typischen VOD-Stream unterscheiden.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie `AdSignalingMode` angeben.

Bei einem FER-Stream sollte der Adobe Primetime-Ad-Entscheidungsserver nicht die Liste von Werbeunterbrechungen bereitstellen, die vor dem Starten der Wiedergabe in die Zeitleiste eingefügt werden müssen. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalisierungsmodus alle Cue-Points aus dem FER-Manifest und wechselt für jeden Cue-Point zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

>[!TIP]
>
>Zusätzlich zu jeder Anforderung, die mit einem Cue-Point verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen auf.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie das `AdSignalingMode` mit `AdvertisingMetadata.setSignalingMode` an.

   Die gültigen Werte sind `DEFAULT`, `SERVER_MAP` und `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >Sie müssen den Anzeigensignalisierungsmodus festlegen, bevor Sie `prepareToPlay` aufrufen. Nachdem TVSDK-Beginn Anzeigen auflösen und auf der Zeitleiste platzieren, werden Änderungen am Anzeigensignalisierungsmodus ignoriert. Legen Sie den Modus fest, wenn Sie das `AuditudeSettings`-Objekt erstellen.

1. Fahren Sie mit der Wiedergabe fort.

<!--<a id="example_6DECA71C3C3B4551805C09A80686552F"></a>-->

```java
MediaPlayer mediaPlayer =  
  new MediaPlayer(getActivity.().getApplicationContext()); 
 
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings.setSignalingMode(AdSignalingMode.MANIFEST_CUES); 
auditudeSettings.setDomain("your-auditude-domain"); 
auditudeSettings.setZoneId("your-auditude-zone-id"); 
auditudeSettings.setMediaId("your-media-id"); 
// set additional targeting parameters or custom parameters 
 
MediaPlayerItemConfig itemConfig =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
MediaResource mediaResource =  
  new MediaResource("https://example.com/media/test_media.m3u8",  
                    MediaResource.Type.HLS, Metadata); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
            // TVSDK is in the PREPARED state, so start the playback 
            mediaPlayer.play(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.COMPLETE ) { 
            // playback has reached the end of stream ( ads included ) 
            // if we want to rewind we can call 
            mediaPlayer.seek(mediaPlayer.getSeekableRange().getBegin()); 
        } 
    } 
}); 
 
mediaPlayer.replaceCurrentResource(mediaResource, itemConfig); 
```
