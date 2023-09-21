---
description: Mit Ereignishandlern können Sie auf TVSDK-Ereignisse reagieren.
title: Implementieren von Ereignis-Listenern und -Rückrufen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Implementieren von Ereignis-Listenern und -Rückrufen {#implement-event-listeners-and-callbacks}

Mit Ereignishandlern können Sie auf TVSDK-Ereignisse reagieren.

Wenn ein Ereignis eintritt, ruft der Ereignismechanismus von TVSDK Ihren registrierten Ereignishandler auf und übergibt ihm die Ereignisinformationen.

TVSDK definiert Listener als öffentliche interne Schnittstellen innerhalb der `MediaPlayer` -Schnittstelle.

Ihre Anwendung muss Ereignis-Listener für alle TVSDK-Ereignisse implementieren, die sich auf Ihre Anwendung auswirken.

1. Bestimmen Sie, auf welche Ereignisse die Anwendung überwachen muss.

   * Erforderliche Ereignisse: Suchen Sie nach allen Wiedergabeereignissen.

     >[!IMPORTANT]
     >
     >Suchen Sie nach dem Ereignis zur Statusänderung, das auftritt, wenn sich der Status des Players auf eine Art ändert, die Sie kennen müssen. Die bereitgestellten Informationen enthalten Fehler, die sich auf die nächsten Schritte Ihres Players auswirken können.

   * Weitere Ereignisse, je nach Anwendung, finden Sie unter events-summary .

1. Implementieren und fügen Sie für jedes Ereignis einen Ereignis-Listener hinzu.

   >[!NOTE]
   >
   >Für die meisten Ereignisse übergibt TVSDK Argumente an die Ereignis-Listener. Diese Werte enthalten Informationen über das Ereignis, die Ihnen bei der Entscheidung helfen können, was Sie als Nächstes tun sollen. Die `MediaPlayerEvent` Auflistung listet alle Ereignisse auf, die `MediaPlayer` Sendungen. Weitere Informationen finden Sie unter events-summary .

   Wenn beispielsweise `mPlayer` ist eine Instanz von `MediaPlayer`können Sie hier einen Ereignis-Listener hinzufügen und strukturieren:

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

## Reihenfolge der Wiedergabeereignisse {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK sendet Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen in der erwarteten Sequenz implementieren.

Die folgenden Beispiele zeigen die Reihenfolge einiger Ereignisse, die während der Wiedergabe auftreten.

Beim erfolgreichen Laden einer Medienressource über `MediaPlayer.replaceCurrentResource`lautet die Reihenfolge der Ereignisse:

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Laden Sie Ihre Medienressource in den Haupt-Thread. Wenn Sie eine Medienressource in einen Hintergrund-Thread laden, kann dieser Vorgang oder nachfolgende Vorgänge einen Fehler auslösen, z. B. `MediaPlayerException`und beenden Sie.

Beim Vorbereiten der Wiedergabe über `MediaPlayer.prepareToPlay`lautet die Reihenfolge der Ereignisse:

1. `MediaPlayerEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` wenn Anzeigen eingefügt wurden.
1. `MediaPlayerEvent.STATUS_CHANGED` mit Status `MediaPlayerStatus.PREPARED`

Bei Live-/linearen Streams lautet die Reihenfolge der Ereignisse während der Wiedergabe, während das Wiedergabefenster wechselt und zusätzliche Möglichkeiten aufgelöst werden:

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` , wenn Anzeigen eingefügt wurden

## Reihenfolge von Werbeintereignissen {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wenn Ihre Wiedergabe Werbung enthält, sendet TVSDK Ereignisse/Benachrichtigungen in allgemein erwarteten Sequenzen. Ihr Player kann Aktionen basierend auf Ereignissen innerhalb der erwarteten Sequenz implementieren.

Beim Abspielen von Anzeigen lautet die Reihenfolge der Ereignisse:

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

Die folgenden Ereignisse werden für jede Anzeige innerhalb der Werbeunterbrechung gesendet:

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

Das folgende Beispiel zeigt eine typische Progression von Anzeigenwiedergabeereignissen:

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

## Reihenfolge der DRM-Ereignisse {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK sendet Digital Rights Management (DRM)-Ereignisse als Reaktion auf DRM-bezogene Vorgänge, z. B. wenn neue DRM-Metadaten verfügbar werden. Ihr Player kann als Reaktion auf diese Ereignisse Aktionen implementieren.

Um über alle DRM-bezogenen Ereignisse benachrichtigt zu werden, suchen Sie nach `MediaPlayerEvent.DRM_METADATA`. TVSDK sendet zusätzliche DRM-Ereignisse über die `DRMManager` -Klasse.

## Reihenfolge der Lader-Ereignisse {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK-Dispatches `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` wenn Ladeereignisse auftreten.
