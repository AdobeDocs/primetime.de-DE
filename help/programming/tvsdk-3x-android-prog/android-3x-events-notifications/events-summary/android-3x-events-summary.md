---
description: Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignisse wartet, die von TVSDK gesendet werden.
title: Übersicht über die Primetime-Player-Ereignisse
exl-id: 3912f140-1600-41fb-9dc4-306646b7cd85
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Übersicht über die Primetime-Player-Ereignisse {#primetime-player-events-summary}

Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignisse wartet, die von TVSDK gesendet werden.

## Veranstaltungen {#events}

TVSDK benachrichtigt Sie beim Auftreten von Ereignissen, auf die Ihre Anwendung reagieren muss. Jedes Ereignis entspricht einer Listener-Klasse mit einer Callback-Methode, die Sie implementieren müssen.

>[!TIP]
>
>Die Ereigniscodes sind die Konstanten der `MediaPlayerEvent`-Enumeration.

`AdBreakCompletedEventListener`

* **** Das bedeutet, dass die Wiedergabe der Werbeunterbrechung abgeschlossen ist.

* **Zu implementierende Rückrufe** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** Das bedeutet, dass während der Wiedergabe eine Werbeunterbrechung übersprungen wurde.

* **Zu implementierende Rückrufe** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** Das bedeutet, dass die Wiedergabe der Werbeunterbrechung gestartet wurde.

* **Zu implementierende Rückrufe** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_START`

`AdClickedEventListener`

* **** Das bedeutet, dass während der Wiedergabe auf eine Anzeige geklickt wurde.

* **Zu implementierende Rückrufe** `onAdClicked(AdClickEvent event)`
* **Ereigniscode** `AD_CLICK`

`AdCompletedEventListener`

* **** Das bedeutet, dass die Wiedergabe der Anzeige abgeschlossen ist.

* **Zu implementierende Rückrufe** `onAdCompleted(AdPlaybackEvent event)`

* **Ereigniscode** `AD_COMPLETE`

`AdProgressEventListener`

* **** bedeutet, den Fortschritt der Berichterstellung während der Wiedergabe zu melden.

* **Zu implementierende Rückrufe** `onAdProgress(AdPlaybackEvent event)`

* **Ereigniscode** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** Die Auflösung von Primetime und Entscheidungsfindung und Auflösung ist abgeschlossen. Dieses Ereignis gilt nur für VOD-Inhalte.

* **Zu implementierende Rückrufe** `onAdResolutionComplete()`

* **Ereigniscode** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** Das bedeutet, dass die Wiedergabe der Anzeige gestartet wurde.

* **Zu implementierende Rückrufe** `onAdStarted(AdPlaybackEvent event)`

* **Ereigniscode** `AD_START`

`AudioUpdatedEventListener`

* **** Das bedeutet, dass ein neuer Audio-Track erkannt wurde.

* **Zu implementierende Rückrufe** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** Das bedeutet, dass der Player mit der Pufferung begonnen hat.

* **Zu implementierende Rückrufe** `onBufferingBegin(BufferEvent event)`

* **Ereigniscode** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** Das bedeutet, dass der Player die Pufferung beendet hat.

* **Zu implementierende Rückrufe** `onBufferingEnd(BufferEvent event)`

* **Ereigniscode** `BUFFERING_END`

`BufferPreparedEventListener`

* **** Das bedeutet, dass der Puffer vorbereitet wird.

* **Zu implementierende Rückrufe** `onBufferPrepared()`

* **Ereigniscode** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** Das bedeutet, dass eine neue Untertitelspur erkannt wurde.

* **Zu implementierende Rückrufe** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** Das bedeutet, dass im Medien-Stream neue DRM-Metadaten erkannt wurden.

* **Zu implementierende Rückrufe** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Ereigniscode** `DRM_METADATA`

`ItemCreatedEventListener`

* **** Das bedeutet, dass ein neues Medienplayer-Element erstellt wurde.

* **Zu implementierende Rückrufe** `onItemCreated(MediaPlayerItemEvent event)`

* **Ereigniscode** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** Das bedeutet, dass für das aktuelle Element neue Ladeinformationen erstellt wurden.

* **Zu implementierende Rückrufe** `onLoadComplete(MediaPlayerItemEvent event)`

* **Ereigniscode** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** Das bedeutet, dass ein neues Segment geladen wurde.

* **Zu implementierende Rückrufe** `onLoadInformation(LoadInformationEvent event)`

* **Ereigniscode** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** Das Hauptmanifest oder die Wiedergabeliste wurde aktualisiert.

* **Zu implementierende Rückrufe** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** Das bedeutet, dass der Vorgang fehlgeschlagen ist.

* **Zu implementierende Rückrufe** `onNotification(NotificationEvent event)`

* **Ereigniscode** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** Das bedeutet, dass der Wiedergabefeld aktualisiert wurde.

* **Zu implementierende Rückrufe** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** Das bedeutet, dass eine neue Wiedergaberate auf dem Bildschirm angezeigt wird.

* **Zu implementierende Rückrufe** `onRatePlaying(PlaybackRateEvent event)`

* **Ereigniscode** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** Das bedeutet, dass das Ratenattribut von MediaPlayer festgelegt wurde.

* **Zu implementierende Rückrufe** `onRateSelected(PlaybackRateEvent event)`

* **Ereigniscode** `RATE_SELECTED`

`PlayStartEventListener`

* **** Das bedeutet, dass die Wiedergabe gestartet wurde.

* **Zu implementierende Rückrufe** `onPlayStart()`

* **Ereigniscode** `PLAY_START`

`ProfileChangeEventListener`

* **** Das bedeutet, dass sich das aktuelle Profil des MediaPlayer geändert hat.

* **Zu implementierende Rückrufe** `onProfileChanged(ProfileEvent event)`

* **Ereigniscode** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** Das bedeutet, dass die Wiedergabe eine Zeitleistenreservierung erreicht hat.

* **Zu implementierende Rückrufe** `onReservationReached(ReservationEvent event)`

* **Ereigniscode** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **** Der Vorgang &quot;Bedeutende Suche&quot;wurde gestartet.

* **Zu implementierende Rückrufe** `onSeekBegin(SeekEvent event)`

* **Ereigniscode** `SEEK_BEGIN`

`SeekEndEventListener`

* **** Das bedeutet, dass der Suchvorgang abgeschlossen ist.

* **Zu implementierende Rückrufe** `onSeekEnd(SeekEvent event)`

* **Ereigniscode** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** Das bedeutet, die Suchposition wurde aufgrund interner Wiedergaberegeln oder externer Geschäftsregeln angepasst.

* **Zu implementierende Rückrufe** `onPositionAdjusted(SeekEvent event)`

* **Ereigniscode** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** Das bedeutet, dass die Größe des Mediums verfügbar ist.

* **Zu implementierende Rückrufe** `onSizeAvailable(SizeAvailableEvent event)`

* **Ereigniscode** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** Das bedeutet, dass sich der MediaPlayer-Status geändert hat.

* **Zu implementierende Rückrufe** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Ereigniscode** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** Das bedeutet, dass sich die Abspielleiste geändert hat.

* **Zu implementierende Rückrufe** `onTimeChanged(TimeChangeEvent event)`

* **Ereigniscode** `TIME_CHANGED`

`TimedEventEventListener`

* **** Das bedeutet, dass der Vorgang mit der für den Vorgang benötigten Zeit abgeschlossen ist.

* **Zu implementierende Rückrufe** `onTimedEvent(TimedEventEvent event)`

* **Ereigniscode** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** Das bedeutet, dass einem Element im Hintergrund neue zeitgesteuerte Metadaten hinzugefügt wurden.

* **Zu implementierende Rückrufe** `onTimedMetadata(TimedMetadataEvent event)`

* **Ereigniscode** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** Das bedeutet, dass im Medien-Stream neue zeitgesteuerte Metadaten erkannt wurden.

* **Zu implementierende Rückrufe** `onTimedMetadata(TimedMetadataEvent event)`

* **Ereigniscode** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** Das bedeutet, dass die Timeline geändert wurde. Anzeigen wurden der Timeline möglicherweise hinzugefügt oder daraus entfernt.

* **Zu implementierende Rückrufe** `onTimelineUpdated(TimelineEvent event)`

* **Ereigniscode** `TIMELINE_UPDATED`
