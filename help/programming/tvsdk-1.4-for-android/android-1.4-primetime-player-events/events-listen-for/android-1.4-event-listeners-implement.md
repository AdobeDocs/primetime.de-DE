---
description: Ereignis-Handler ermöglichen es TVSDK, auf Ereignisse zu reagieren.
title: Implementieren von Ereignis-Listenern und -Rückrufen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Implementieren von Ereignis-Listenern und -Rückrufen{#implement-event-listeners-and-callbacks}

Ereignis-Handler ermöglichen es TVSDK, auf Ereignisse zu reagieren.

Wenn ein Ereignis eintritt, ruft der Ereignismechanismus von TVSDK Ihren registrierten Ereignishandler auf und übergibt die Ereignisinformationen an den Handler.

TVSDK definiert Listener als öffentliche interne Schnittstellen in der `MediaPlayer` -Schnittstelle.

Ihre Anwendung muss Ereignis-Listener für TVSDK-Ereignisse implementieren, die sich auf Ihre Anwendung auswirken.

Eine vollständige Liste der Ereignisse für Videoanalysen finden Sie unter Tracking der Core-Videowiedergabe.

1. Bestimmen Sie, auf welche Ereignisse die Anwendung überwachen muss.

   * **Erforderliche Ereignisse**: Suchen Sie nach allen Wiedergabeereignissen.

     >[!IMPORTANT]
     >
     >Das Wiedergabeereignis `onStateChanged` stellt den Player-Status bereit, einschließlich Fehlern. Jeder Status kann sich auf den nächsten Schritt Ihres Players auswirken

   * **Andere Ereignisse**: Optional, je nach Anwendung.

     Wenn Sie beispielsweise Werbung in Ihre Wiedergabe integrieren, implementieren Sie die AdPlaybackEventListener-Rückrufe.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   TVSDK gibt Parameterwerte an Ihre Ereignis-Listener-Rückrufe zurück. Diese Werte enthalten relevante Informationen zum Ereignis, das Sie in Ihren Listenern verwenden können, um geeignete Aktionen durchzuführen.

   `MediaPlayer.EventListener` listet alle Callback-Schnittstellen auf. Jede Schnittstelle zeigt den Callback-Namen und die Parameter an, die für jedes Ereignis zurückgegeben werden.

   Beispiel:

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. Registrieren Sie Ihre Callback-Listener bei der `MediaPlayer` -Objekt mithilfe von `MediaPlayer.addEventListener`.

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## Reihenfolge der Wiedergabeereignisse {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK sendet Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignisse, die Wiedergabeereignisse enthalten.

* Beim erfolgreichen Laden einer Medienressource über `MediaPlayer.replaceCurrentResource`lautet die Reihenfolge der Ereignisse:

1. `MediaPlayer.PlaybackEventListener.onStateChanged` mit Status `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` mit Status `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>Laden Sie Ihre Medienressource in den Haupt-Thread. Wenn Sie eine Medienressource in einen Hintergrund-Thread laden, kann dieser Vorgang oder nachfolgende TVSDK-Vorgänge oder beides einen Fehler auslösen (z. B. `IllegalStateException`) und beenden Sie.

* Beim Vorbereiten der Wiedergabe über `MediaPlayer.prepareToPlay`lautet die Reihenfolge der Ereignisse:

1. `MediaPlayer.PlaybackEventListener.onStateChanged` mit Status `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` wenn Anzeigen eingefügt wurden.
1. `MediaPlayer.PlaybackEventListener.onStateChanged` mit Status `MediaPlayerStatus.PREPARED`

* Bei Live-/linearen Streams lautet die Reihenfolge der Ereignisse während der Wiedergabe, während das Wiedergabefenster wechselt und zusätzliche Möglichkeiten aufgelöst werden:

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` , wenn Anzeigen eingefügt wurden
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` , wenn Anzeigen eingefügt wurden

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

## Reihenfolge von Werbeintereignissen {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignisse:

* `AdPlaybackEventListener.onAdBreakStart`
* Folgendes wird für jede Anzeige in der Werbeunterbrechung gesendet:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (mehrmals während der Wiedergabe einer Anzeige)
   * `AdPlaybackEventListener.onAdClick` (für jeden Klick)
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

Das folgende Beispiel zeigt eine typische Progression von Anzeigenwiedergabeereignissen:

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

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignisse:

* `AdPlaybackEventListener.onAdBreakStart`
* Folgendes wird für jede Anzeige in der Werbeunterbrechung gesendet:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (mehrmals während der Wiedergabe einer Anzeige)
   * `AdPlaybackEventListener.onAdClick` (für jeden Klick)
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

Das folgende Beispiel zeigt eine typische Progression von Anzeigenwiedergabeereignissen:

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

## QoS-Ereignisse {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK sendet Servicequalitätsereignisse (QoS), um Ihre Anwendung über Ereignisse zu informieren, die die Berechnung von QoS-Statistiken beeinflussen könnten, z. B. Pufferungs- und Suchereignisse.

Das folgende Beispiel zeigt eine typische Progression dieser Ereignisse:

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

TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann als Reaktion auf diese Ereignisse Aktionen implementieren.

Um über alle DRM-bezogenen Ereignisse benachrichtigt zu werden, suchen Sie nach `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK sendet zusätzliche DRM-Ereignisse über die `DRMManager` -Klasse.

Das folgende Beispiel zeigt eine typische Progression:

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## Ladeereignisse {#section_5638F8EDACCE422A9425187484D39DCC}

Ihr Player kann Aktionen basierend auf den folgenden Ereignissen implementieren:

| Ereignis | Bedeutung |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | Das Laden der Medienressource wurde erfolgreich abgeschlossen. |
| `onError` | Beim Laden der Medienressource ist ein Problem aufgetreten. |
