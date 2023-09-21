---
description: Die Wiederholung eines vollständigen Ereignisses (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Maßnahmen ergreifen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
title: Aktivieren von Anzeigen bei vollständiger Ereigniswiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Aktivieren von Anzeigen bei vollständiger Ereigniswiedergabe {#enable-ads-in-full-event-replay-overview}

Die Wiederholung eines vollständigen Ereignisses (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Maßnahmen ergreifen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird ein `EXT-X-ENDLIST` -Tag an das Live-Manifest angehängt. Bei HLS muss die Variable `EXT-X-ENDLIST` -Tag bedeutet, dass der Stream ein VOD-Stream ist. Um Anzeigen richtig einzufügen, kann TVSDK diesen Stream nicht automatisch von einem typischen VOD-Stream unterscheiden.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie die `AdSignalingMode`.

Bei einem FER-Stream sollte der Adobe Primetime-Ad Decisioning-Server nicht die Liste der Werbeunterbrechungen bereitstellen, die in die Timeline eingefügt werden müssen, bevor die Wiedergabe gestartet wird. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalmodus alle Cue-Punkte aus dem FER-Manifest und geht für jeden Cue-Punkt zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

>[!TIP]
>
>Zusätzlich zu jeder Anfrage, die mit einem Cue-Punkt verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen vor.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie die `AdSignalingMode` mithilfe von `AdvertisingMetadata.setSignalingMode`.

   Die gültigen Werte sind `DEFAULT`, `SERVER_MAP`, und `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >Sie müssen den Anzeigenanzeigemodus festlegen, bevor Sie `prepareToPlay`. Wenn TVSDK beginnt, Anzeigen aufzulösen und auf der Timeline zu platzieren, werden Änderungen am Anzeigenanzeigemodus ignoriert. Legen Sie den Modus fest, wenn Sie die `AuditudeSettings` -Objekt.

1. Wiedergabe fortsetzen.

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
