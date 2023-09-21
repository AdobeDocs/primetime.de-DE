---
description: Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignisse wartet, die von TVSDK gesendet werden.
title: Übersicht über die Primetime-Player-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
>Die Ereigniscodes sind die Konstanten der `MediaPlayerEvent` enum.

`AdBreakCompletedEventListener`

* **Bedeutung** Die Wiedergabe der Werbeunterbrechung ist abgeschlossen.

* **Zu implementierende Rückrufe** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **Bedeutung** Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen.

* **Zu implementierende Rückrufe** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **Bedeutung** Die Wiedergabe der Werbeunterbrechung wurde gestartet.

* **Zu implementierende Rückrufe** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Ereigniscode** `AD_BREAK_START`

`AdClickedEventListener`

* **Bedeutung** Während der Wiedergabe wurde auf eine Anzeige geklickt.

* **Zu implementierende Rückrufe** `onAdClicked(AdClickEvent event)`
* **Ereigniscode** `AD_CLICK`

`AdCompletedEventListener`

* **Bedeutung** Die Wiedergabe der Anzeige ist abgeschlossen.

* **Zu implementierende Rückrufe** `onAdCompleted(AdPlaybackEvent event)`

* **Ereigniscode** `AD_COMPLETE`

`AdProgressEventListener`

* **Bedeutung** Berichtsfortschritt während der Wiedergabe

* **Zu implementierende Rückrufe** `onAdProgress(AdPlaybackEvent event)`

* **Ereigniscode** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **Bedeutung** Die Primetime-Anzeigenentscheidung und -auflösung ist abgeschlossen. Dieses Ereignis gilt nur für VOD-Inhalte.

* **Zu implementierende Rückrufe** `onAdResolutionComplete()`

* **Ereigniscode** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **Bedeutung** Die Wiedergabe der Anzeige wurde gestartet.

* **Zu implementierende Rückrufe** `onAdStarted(AdPlaybackEvent event)`

* **Ereigniscode** `AD_START`

`AudioUpdatedEventListener`

* **Bedeutung** Ein neuer Audio-Track wurde erkannt.

* **Zu implementierende Rückrufe** `onAudioUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **Bedeutung** Der Player hat mit der Pufferung begonnen.

* **Zu implementierende Rückrufe** `onBufferingBegin(BufferEvent event)`

* **Ereigniscode** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **Bedeutung** Der Player hat die Pufferung beendet.

* **Zu implementierende Rückrufe** `onBufferingEnd(BufferEvent event)`

* **Ereigniscode** `BUFFERING_END`

`BufferPreparedEventListener`

* **Bedeutung** Der Puffer wird vorbereitet.

* **Zu implementierende Rückrufe** `onBufferPrepared()`

* **Ereigniscode** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **Bedeutung** Ein neuer Untertitelpfad wurde erkannt.

* **Zu implementierende Rückrufe** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **Bedeutung** Im Medien-Stream wurden neue DRM-Metadaten erkannt.

* **Zu implementierende Rückrufe** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Ereigniscode** `DRM_METADATA`

`ItemCreatedEventListener`

* **Bedeutung** Ein neues Medienplayer-Element wurde erstellt.

* **Zu implementierende Rückrufe** `onItemCreated(MediaPlayerItemEvent event)`

* **Ereigniscode** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **Bedeutung** Für das aktuelle Element wurden neue Ladeinformationen erstellt.

* **Zu implementierende Rückrufe** `onLoadComplete(MediaPlayerItemEvent event)`

* **Ereigniscode** `ITEM_UPDATED`

`LoadInformationEventListener`

* **Bedeutung** Ein neues Segment wurde geladen.

* **Zu implementierende Rückrufe** `onLoadInformation(LoadInformationEvent event)`

* **Ereigniscode** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **Bedeutung** Das Hauptmanifest oder die Wiedergabeliste wurde aktualisiert.

* **Zu implementierende Rückrufe** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `MANIFEST_UPDATED`

`NotificationEventListener`

* **Bedeutung** Der Vorgang ist fehlgeschlagen.

* **Zu implementierende Rückrufe** `onNotification(NotificationEvent event)`

* **Ereigniscode** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **Bedeutung** Der Wiedergabebereich wurde aktualisiert.

* **Zu implementierende Rückrufe** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Ereigniscode** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **Bedeutung** Auf dem Bildschirm wird eine neue Wiedergaberate angezeigt.

* **Zu implementierende Rückrufe** `onRatePlaying(PlaybackRateEvent event)`

* **Ereigniscode** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **Bedeutung** Das Ratenattribut von MediaPlayer wurde festgelegt.

* **Zu implementierende Rückrufe** `onRateSelected(PlaybackRateEvent event)`

* **Ereigniscode** `RATE_SELECTED`

`PlayStartEventListener`

* **Bedeutung** Die Wiedergabe wurde gestartet.

* **Zu implementierende Rückrufe** `onPlayStart()`

* **Ereigniscode** `PLAY_START`

`ProfileChangeEventListener`

* **Bedeutung** Das aktuelle Profil des MediaPlayer wurde geändert.

* **Zu implementierende Rückrufe** `onProfileChanged(ProfileEvent event)`

* **Ereigniscode** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **Bedeutung** Die Wiedergabe erreichte eine Timeline-Reservierung.

* **Zu implementierende Rückrufe** `onReservationReached(ReservationEvent event)`

* **Ereigniscode** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **Bedeutung** Der Suchvorgang wurde gestartet.

* **Zu implementierende Rückrufe** `onSeekBegin(SeekEvent event)`

* **Ereigniscode** `SEEK_BEGIN`

`SeekEndEventListener`

* **Bedeutung** Der Suchvorgang wurde abgeschlossen.

* **Zu implementierende Rückrufe** `onSeekEnd(SeekEvent event)`

* **Ereigniscode** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **Bedeutung** Die Suchposition wurde aufgrund interner Wiedergaberegeln oder externer Geschäftsregeln angepasst.

* **Zu implementierende Rückrufe** `onPositionAdjusted(SeekEvent event)`

* **Ereigniscode** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **Bedeutung** Die Größe des Mediums ist verfügbar.

* **Zu implementierende Rückrufe** `onSizeAvailable(SizeAvailableEvent event)`

* **Ereigniscode** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **Bedeutung** Der MediaPlayer-Status hat sich geändert.

* **Zu implementierende Rückrufe** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Ereigniscode** `STATUS_CHANGED`

`TimeChangeEventListener`

* **Bedeutung** Die Abspielleiste hat sich geändert.

* **Zu implementierende Rückrufe** `onTimeChanged(TimeChangeEvent event)`

* **Ereigniscode** `TIME_CHANGED`

`TimedEventEventListener`

* **Bedeutung** Der Vorgang ist mit der für den Vorgang benötigten Zeit abgeschlossen.

* **Zu implementierende Rückrufe** `onTimedEvent(TimedEventEvent event)`

* **Ereigniscode** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **Bedeutung** Ein Element im Hintergrund wurde um neue zeitgesteuerte Metadaten erweitert.

* **Zu implementierende Rückrufe** `onTimedMetadata(TimedMetadataEvent event)`

* **Ereigniscode** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **Bedeutung** Im Medien-Stream wurden neue zeitgesteuerte Metadaten erkannt.

* **Zu implementierende Rückrufe** `onTimedMetadata(TimedMetadataEvent event)`

* **Ereigniscode** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **Bedeutung** Die Timeline wurde geändert. Anzeigen wurden der Timeline möglicherweise hinzugefügt oder aus ihr entfernt.

* **Zu implementierende Rückrufe** `onTimelineUpdated(TimelineEvent event)`

* **Ereigniscode** `TIMELINE_UPDATED`
