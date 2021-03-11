---
description: Ereignisse von TVSDK geben den Player-Status, auftretende Fehler, den Abschluss von angeforderten Aktionen an, z. B. die Videowiedergabe oder implizit auftretende Aktionen, z. B. das Ausfüllen einer Anzeige.
title: Primetime Player-Ereignis suchen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Übersicht {#implement-event-listeners-and-callbacks-overview}

Ereignis-Handler ermöglichen es TVSDK, auf Ereignis zu reagieren. Wenn ein Ereignis auftritt, ruft der Ereignis-Mechanismus von TVSDK Ihren registrierten Ereignis-Handler auf und übergibt die Ereignis-Informationen an den Handler.

Die Flash Runtime bietet einen allgemeinen Ereignis-Mechanismus, den das TVSDK auch verwendet und eine Reihe von benutzerdefinierten Ereignissen definiert. Ihre Anwendung muss Ereignis-Listener für TVSDK-Ereignis implementieren, die Ihre Anwendung betreffen.

Eine vollständige Liste der Ereignis für Videoanalysen finden Sie unter [Core-Videowiedergabe verfolgen](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html).

1. Bestimmen Sie, auf welche Ereignis Ihre Anwendung hören muss.

   * **Erforderliche Ereignis**: Suchen Sie nach allen Ereignissen für die Wiedergabe.

      >[!IMPORTANT]
      >
      >Das play-Ereignis `MediaPlayerStatusChangeEvent.STATUS_CHANGE` stellt den Player-Status einschließlich Fehler bereit. Jeder Status kann sich auf den nächsten Schritt Ihres Spielers auswirken.

   * **Andere Ereignisse**: Optional, je nach Anwendung.

      Wenn Sie z. B. Werbung in Ihre Wiedergabe integrieren, sollten Sie alle `AdBreakPlaybackEvent`- und `AdPlaybackEvent`-Ereignis abhören.

1. Implementieren Sie Ereignis-Listener für jedes Ereignis.

   TVSDK gibt Parameterwerte an Ihre Ereignis-Listener-Rückrufe zurück. Diese Werte liefern relevante Informationen über das Ereignis, das Sie in Ihren Listenern verwenden können, um entsprechende Aktionen durchzuführen.

   Die `Event`-Klasse Liste alle Callback-Schnittstellen. Jede Schnittstelle zeigt die Parameter an, die für diese Schnittstelle zurückgegeben werden.

   Beispiel:

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Registrieren Sie Ihre Callback-Listener mit dem `MediaPlayer`-Objekt, indem Sie `MediaPlayer.addEventListener` verwenden.

   `MediaPlayer` extension  `flash.events.IEventDispatcher`, das zu den Core-Dateien des Flash-Players gehört und die Funktionen  `addEventListener` und  `removeEventListener`Funktionen enthält.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


