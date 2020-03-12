---
description: Ereignis-Handler ermöglichen es TVSDK, auf Ereignis zu reagieren.
seo-description: Ereignis-Handler ermöglichen es TVSDK, auf Ereignis zu reagieren.
seo-title: Implementieren von Ereignis-Listenern und -Rückrufen
title: Implementieren von Ereignis-Listenern und -Rückrufen
uuid: 6b7859a4-55f9-48b1-b1f1-7b79bc92610a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Implementieren von Ereignis-Listenern und -Rückrufen{#implement-event-listeners-and-callbacks}

Ereignis-Handler ermöglichen es TVSDK, auf Ereignis zu reagieren.

Wenn ein Ereignis auftritt, ruft der Ereignis-Mechanismus von TVSDK Ihren registrierten Ereignis-Handler auf und übergibt die Ereignis-Informationen an den Handler.

TVSDK definiert Listener als öffentliche interne Schnittstellen in der `MediaPlayer` Schnittstelle.

Ihre Anwendung muss Ereignis-Listener für TVSDK-Ereignis implementieren, die Ihre Anwendung betreffen.

Eine vollständige Liste der Ereignis für Videoanalysen finden Sie unter Core-Video-Wiedergabe verfolgen.

1. Bestimmen Sie, auf welche Ereignis Ihre Anwendung hören muss.

   * **Erforderliche Ereignis**: Suchen Sie nach allen Ereignissen für die Wiedergabe.

      >[!IMPORTANT]
      >
      >Das play-Ereignis `onStateChanged` stellt den Player-Status einschließlich Fehler bereit. Jeder Status kann sich auf den nächsten Schritt Ihres Spielers auswirken

   * **Andere Ereignisse**: Optional, je nach Anwendung.

      Wenn Sie z. B. Werbung in Ihre Wiedergabe integrieren, implementieren Sie die AdPlaybackEventListener-Rückrufe.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   TVSDK gibt Parameterwerte an Ihre Ereignis-Listener-Rückrufe zurück. Diese Werte liefern relevante Informationen über das Ereignis, das Sie in Ihren Listenern verwenden können, um entsprechende Aktionen durchzuführen.

   `MediaPlayer.EventListener` Liste aller Callback-Schnittstellen. Jede Schnittstelle zeigt den Rückruffamen und die Parameter an, die für jedes Ereignis zurückgegeben werden.

   Beispiel:

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. Registrieren Sie Ihre Callback-Listener mit dem `MediaPlayer` Objekt, indem Sie `MediaPlayer.addEventListener`.

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## Reihenfolge der Ereignis {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK sendet Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignis, die Ereignis für die Wiedergabe enthalten.

* Beim erfolgreichen Laden einer Medienressource `MediaPlayer.replaceCurrentResource`lautet die Reihenfolge der Ereignis:

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>Laden Sie Ihre Medienressource in den Hauptthread. Wenn Sie eine Medienressource in einen Hintergrund-Thread laden, kann dieser Vorgang oder nachfolgende TVSDK-Vorgänge oder beides einen Fehler auslösen (z. B. `IllegalStateException`) und beenden.

* Beim Vorbereiten der Wiedergabe durch `MediaPlayer.prepareToPlay`lautet die Reihenfolge der Ereignis:

1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` wenn Anzeigen eingefügt wurden.
1. `MediaPlayer.PlaybackEventListener.onStateChanged` with state `MediaPlayerStatus.PREPARED`

* Bei Live-/linearen Streams lautet die Reihenfolge der Ereignis während der Wiedergabe, während das Wiedergabefenster erweitert und weitere Möglichkeiten aufgelöst werden, wie folgt:

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` wenn Anzeigen eingefügt wurden
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden

Das folgende Beispiel zeigt eine typische Progression von Ereignissen:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK,  
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() {...} 
    @Override 
    public void onUpdated() {...} 
    @Override 
    public void onPlayStart() {...} 
    @Override 
    public void onPlayComplete() {...} 
    @Override 
    public void onSizeAvailable(long height, long width) {...} 
    @Override 
    public void onStateChanged(MediaPlayer.PlayerState state,  
      MediaPlayerNotification notification) {...} 
});
```

## Reihenfolge der Ereignis {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignis:

* `AdPlaybackEventListener.onAdBreakStart`
* Für jede Anzeige in der Werbeunterbrechung werden die folgenden Meldungen ausgelöst:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (mehrere Male während der Wiedergabe einer Anzeige)
   * `AdPlaybackEventListener.onAdClick` (für jeden Klick)
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

Das folgende Beispiel zeigt eine typische Progression von Ereignissen zur Anzeigenwiedergabe:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignis:

* `AdPlaybackEventListener.onAdBreakStart`
* Für jede Anzeige in der Werbeunterbrechung werden die folgenden Meldungen ausgelöst:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (mehrere Male während der Wiedergabe einer Anzeige)
   * `AdPlaybackEventListener.onAdClick` (für jeden Klick)
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

Das folgende Beispiel zeigt eine typische Progression von Ereignissen zur Anzeigenwiedergabe:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

## QoS-Ereignis {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der QoS-Statistiken beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.

Das folgende Beispiel zeigt eine typische Progression dieser Ereignis:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.QOS,  
  new MediaPlayer.QOSEventListener(){ 
    //For buffering activity 
    @Override 
    public void onBufferStart() 
    @Override 
    public void onBufferComplete() 
    // For seeking 
    @Override 
    public void onSeekStart() 
    @Override 
    public void onSeekComplete(long adjustedTime) 
    @Override 
    public void onLoadComplete (MediaPlayerItem mediaplayeritem) 
    @Override 
    public void onLoadInfo(LoadInfo loadInfo) 
    @Override 
    public void onOperationFailed(MediaPlayerNotification.Warning warning) 
});
```

## DRM-Ereignisse {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann entsprechend diesen Ereignissen Aktionen implementieren.

Um über alle DRM-bezogenen Ereignis informiert zu werden, suchen Sie nach `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK sendet zusätzliche DRM-Ereignis über die `DRMManager` Klasse.

Das folgende Beispiel zeigt eine typische Progression:

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## Loader-Ereignis {#section_5638F8EDACCE422A9425187484D39DCC}

Ihr Player kann Aktionen auf der Grundlage der folgenden Ereignis implementieren:

| Ereignis | Bedeutung |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | Laden der Medienressource erfolgreich abgeschlossen. |
| `onError` | Beim Laden der Medienressource ist ein Problem aufgetreten. |

