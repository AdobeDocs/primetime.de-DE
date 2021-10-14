---
description: Ereignisse von TVSDK geben den Status des Players, aufgetretene Fehler, den Abschluss von angeforderten Aktionen an, z. B. einen Videostart oder implizit auftretende Aktionen, z. B. das Abschließen einer Anzeige.
title: Suchen nach Primetime-Player-Ereignissen
exl-id: 3a740245-a9e1-4e36-8761-f9f4b4e85b93
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Übersicht {#implement-event-listeners-and-callbacks-overview}

Ereignis-Handler ermöglichen es TVSDK, auf Ereignisse zu reagieren. Wenn ein Ereignis eintritt, ruft der Ereignismechanismus von TVSDK Ihren registrierten Ereignishandler auf und übergibt die Ereignisinformationen an den Handler.

Flash Runtime bietet einen allgemeinen Ereignismechanismus, den das TVSDK ebenfalls verwendet und eine Reihe benutzerspezifischer Ereignisse definiert. Ihre Anwendung muss Ereignis-Listener für TVSDK-Ereignisse implementieren, die sich auf Ihre Anwendung auswirken.

1. Bestimmen Sie, auf welche Ereignisse die Anwendung überwachen muss.

   * **Erforderliche Ereignisse**: Suchen Sie nach allen Wiedergabeereignissen.

      >[!IMPORTANT]
      >
      >Das Wiedergabeereignis `MediaPlayerStatusChangeEvent.STATUS_CHANGE` liefert den Player-Status, einschließlich Fehlern. Jeder Status kann sich auf den nächsten Schritt Ihres Players auswirken.

   * **Weitere Ereignisse**: Optional, je nach Anwendung.

      Wenn Sie z. B. Werbung in Ihre Wiedergabe integrieren, sollten Sie alle `AdBreakPlaybackEvent`- und `AdPlaybackEvent`-Ereignisse überwachen.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   TVSDK gibt Parameterwerte an Ihre Ereignis-Listener-Rückrufe zurück. Diese Werte enthalten relevante Informationen zum Ereignis, das Sie in Ihren Listenern verwenden können, um geeignete Aktionen durchzuführen.

   Die Klasse `Event` listet alle Callback-Schnittstellen auf. Jede Schnittstelle zeigt die Parameter an, die für diese Schnittstelle zurückgegeben werden.

   Beispiel:

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Registrieren Sie Ihre Callback-Listener mit dem `MediaPlayer` -Objekt, indem Sie `MediaPlayer.addEventListener` verwenden.

   `MediaPlayer` erweitert  `flash.events.IEventDispatcher`, ist Teil der Kerndateien des Flash-Players und umfasst die Funktionen  `addEventListener` und  `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```
