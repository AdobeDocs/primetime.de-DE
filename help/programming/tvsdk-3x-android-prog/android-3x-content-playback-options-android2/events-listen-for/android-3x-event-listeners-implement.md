---
description: Mit Ereignis-Handlern können Sie auf TVSDK-Ereignis reagieren.
seo-description: Mit Ereignis-Handlern können Sie auf TVSDK-Ereignis reagieren.
seo-title: Implementieren von Ereignis-Listenern und -Rückrufen
title: Implementieren von Ereignis-Listenern und -Rückrufen
uuid: f186b39e-e634-4f64-977d-279147d76c5c
translation-type: tm+mt
source-git-commit: 1034a0520590777cc0930d2f732741202bc3bc04
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Implementieren von Ereignis-Listenern und -Rückrufen {#implement-event-listeners-and-callbacks}

Mit Ereignis-Handlern können Sie auf TVSDK-Ereignis reagieren.

Wenn ein Ereignis auftritt, ruft der Ereignis-Mechanismus von TVSDK Ihren registrierten Ereignis-Handler auf und übergibt ihm die Informationen zum Ereignis.

TVSDK definiert Listener als öffentliche interne Schnittstellen innerhalb der `MediaPlayer`-Schnittstelle.

Ihre Anwendung muss Ereignis-Listener für alle TVSDK-Ereignis implementieren, die Ihre Anwendung betreffen.

1. Bestimmen Sie, auf welche Ereignis Ihre Anwendung achten muss.

   * Erforderliche Ereignis: Suchen Sie nach allen Ereignissen für die Wiedergabe.

      >[!IMPORTANT]
      >
      >Suchen Sie nach dem Ereignis zur Statusänderung, das auftritt, wenn sich der Status des Spielers auf eine Art ändert, die Sie kennen müssen. Die bereitgestellten Informationen enthalten Fehler, die sich möglicherweise auf die nächsten Schritte Ihres Players auswirken können.

   * Weitere Ereignisse finden Sie in Abhängigkeit von Ihrer Anwendung unter [Übersicht über die Primetime-Player-Ereignis](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

1. Implementieren Sie einen Ereignis-Listener für jedes Ereignis und fügen Sie ihn hinzu.

   Für die meisten Ereignisse übergibt TVSDK Argumente an die Ereignis-Listener. Diese Werte liefern Informationen über das Ereignis, mit dem Sie entscheiden können, was als Nächstes zu tun ist. Die `MediaPlayerEvent`-Auflistung Liste alle Ereignis, die `MediaPlayer` auslöst. Weitere Informationen finden Sie unter [Übersicht über die Primetime-Player-Ereignis](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   Wenn `mPlayer` beispielsweise eine Instanz von `MediaPlayer` ist, können Sie wie einen Ereignis-Listener hinzufügen und strukturieren:

   ```java
   mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() { 
       @Override 
       public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
           event.getMetadata(); 
           if (event.getMetadata() != null) {/* Do something */} 
           if (event.getStatus() == MediaPlayerStatus.IDLE) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.INITIALIZED) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.PREPARED) {/* Do something */} 
       } 
   }); 
   ```

## Reihenfolge der Wiedergabe-Ereignis {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK sendet Ereignis/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen in der erwarteten Sequenz implementieren.

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignis, die während der Wiedergabe auftreten.

Beim erfolgreichen Laden einer Medienressource über `MediaPlayer.replaceCurrentResource` lautet die Reihenfolge der Ereignis:

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Laden Sie Ihre Medienressource in den Hauptthread. Wenn Sie eine Medienressource in einen Hintergrund-Thread laden, kann dieser Vorgang oder nachfolgende Vorgänge einen Fehler auslösen, z. B. `MediaPlayerException`, und beenden.

Beim Vorbereiten der Wiedergabe über `MediaPlayer.prepareToPlay` lautet die Reihenfolge der Ereignis:

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden.
1. `MediaPlayerEvent.STATUS_CHANGED` mit Status  `MediaPlayerStatus.PREPARED`

Bei Live-/linearen Streams lautet die Reihenfolge der Ereignis während der Wiedergabe, während das Wiedergabefenster erweitert und weitere Möglichkeiten aufgelöst werden, wie folgt:

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden

## Reihenfolge der Ereignis für Werbung {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen auf der Grundlage von Ereignissen innerhalb der erwarteten Sequenz implementieren.

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignis:

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

Die folgenden Ereignis werden für jede Anzeige innerhalb der Werbeunterbrechung gesendet:

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

Das folgende Beispiel zeigt eine typische Progression von Ereignissen zur Anzeigenwiedergabe:

```
mediaPlayer.addEventListener(MediaPlayerEvent.AD_RESOLUTION_COMPLETE, new AdResolutionCompleteEventListener() { 
        @Override 
        public void onAdResolutionComplete() { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_START, new AdBreakStartedEventListener() { 
         @Override 
        public void onAdBreakStarted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_START, new AdStartedEventListener() { 
         @Override 
        public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_PROGRESS, new AdProgressEventListener() { 
         @Override 
         public void onAdProgress(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_COMPLETE, new AdCompletedEventListener() { 
         @Override 
         public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_COMPLETE, new AdBreakCompletedEventListener() { 
         @Override 
         public void onAdBreakCompleted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
Below event is for tracking ad clicks. 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_CLICK, new AdClickedEventListener() { 
         @Override 
         public void onAdClicked(AdClickEvent adClickEvent) { ... } 
    });
```

## Reihenfolge der DRM-Ereignis {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK sendet DRM-Ereignis (Digital Rights Management) als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann entsprechend diesen Ereignissen Aktionen implementieren.

Um über alle DRM-bezogenen Ereignis informiert zu werden, suchen Sie nach `MediaPlayerEvent.DRM_METADATA`. TVSDK sendet zusätzliche DRM-Ereignis über die `DRMManager`-Klasse.

## Reihenfolge der Lader-Ereignis {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK löst `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` aus, wenn Lader-Ereignis auftreten.