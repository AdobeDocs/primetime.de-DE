---
description: Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.
seo-description: Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.
seo-title: Übersicht zu Primetime-Player-Ereignissen
title: Übersicht zu Primetime-Player-Ereignissen
uuid: b2ff74f2-c373-42da-a717-2f0550cbcb7f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht zu Primetime-Player-Ereignissen {#primetime-player-events-summary}

Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.

## Ereignisse {#events}

TVSDK benachrichtigt Sie, wenn Ereignis auftreten, auf die Ihre Anwendung reagieren muss. Jedes Ereignis entspricht einer Listener-Klasse mit einer Rückrufmethode, die Sie implementieren müssen.

>[!TIP]
>
>Die Ereignis-Codes sind die Konstanten der `MediaPlayerEvent` Enum.

`AdBreakCompletedEventListener`

* **Das bedeutet** , dass die Wiedergabe der Werbeunterbrechung abgeschlossen ist.

* **Rückruf zur Implementierung**`onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **Ereignis-Code**`AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **Das bedeutet** , dass eine Werbeunterbrechung während der Wiedergabe übersprungen wurde.

* **Rückruf zur Implementierung**`onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **Ereignis-Code**`AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **Das bedeutet** , dass die Wiedergabe der Werbeunterbrechung begonnen hat.

* **Rückruf zur Implementierung**`onAdBreakStarted(AdBreakPlaybackEvent event)`

* **Ereignis-Code**`AD_BREAK_START`

`AdClickedEventListener`

* **Das bedeutet** , dass während der Wiedergabe auf eine Anzeige geklickt wurde.

* **Rückruf zur Implementierung**`onAdClicked(AdClickEvent event)`
* **Ereignis-Code**`AD_CLICK`

`AdCompletedEventListener`

* **Das bedeutet** , dass die Wiedergabe der Anzeige abgeschlossen ist.

* **Rückruf zur Implementierung**`onAdCompleted(AdPlaybackEvent event)`

* **Ereignis-Code**`AD_COMPLETE`

`AdProgressEventListener`

* **Das bedeutet** , dass der Berichte während der Wiedergabe fortfährt.

* **Rückruf zur Implementierung**`onAdProgress(AdPlaybackEvent event)`

* **Ereignis-Code**`AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **Das bedeutet** , dass Primetime und Entscheidungsfindung und Auflösung abgeschlossen sind. Dieses Ereignis gilt nur für VOD-Inhalte.

* **Rückruf zur Implementierung**`onAdResolutionComplete()`

* **Ereignis-Code**`AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **Das bedeutet** , dass die Wiedergabe der Anzeige gestartet wurde.

* **Rückruf zur Implementierung**`onAdStarted(AdPlaybackEvent event)`

* **Ereignis-Code**`AD_START`

`AudioUpdatedEventListener`

* **Das bedeutet** , dass eine neue Audiospur erkannt wurde.

* **Rückruf zur Implementierung**`onAudioUpdated(MediaPlayerItemEvent event)`

* **Ereignis-Code**`AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **Das bedeutet** Der Spieler hat mit der Pufferung begonnen.

* **Rückruf zur Implementierung**`onBufferingBegin(BufferEvent event)`

* **Ereignis-Code**`BUFFERING_BEGIN`

`BufferingEndEventListener`

* **Das heißt** , der Spieler hat die Pufferung beendet.

* **Rückruf zur Implementierung**`onBufferingEnd(BufferEvent event)`

* **Ereignis-Code**`BUFFERING_END`

`BufferPreparedEventListener&#39;

* **Das bedeutet** Der Puffer ist vorbereitet.

* **Rückruf zur Implementierung**`onBufferPrepared()`

* **Ereignis-Code**`BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **Das bedeutet** , dass eine neue Beschriftungsspur erkannt wurde.

* **Rückruf zur Implementierung**`onCaptionsUpdated(MediaPlayerItemEvent event)`

* **Ereignis-Code**`CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **Das bedeutet** , dass im Medienstream neue DRM-Metadaten erkannt wurden.

* **Rückruf zur Implementierung**`onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **Ereignis-Code**`DRM_METADATA`

`ItemCreatedEventListener`

* **Das bedeutet** , dass ein neues Medienplayer-Element erstellt wurde.

* **Rückruf zur Implementierung**`onItemCreated(MediaPlayerItemEvent event)`

* **Ereignis-Code**`ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **Das bedeutet** Für das aktuelle Element wurden neue Ladeinformationen erstellt.

* **Rückruf zur Implementierung**`onLoadComplete(MediaPlayerItemEvent event)`

* **Ereignis-Code**`ITEM_UPDATED`

`LoadInformationEventListener`

* **Das bedeutet** , dass ein neues Segment geladen wurde.

* **Rückruf zur Implementierung**`onLoadInformation(LoadInformationEvent event)`

* **Ereignis-Code**`LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **Das bedeutet** , dass das Hauptmanifest oder die Wiedergabeliste aktualisiert wurde.

* **Rückruf zur Implementierung**`onMainManifestUpdated(MediaPlayerItemEvent event)`

* **Ereignis-Code**`MANIFEST_UPDATED`

`NotificationEventListener`

* **Das bedeutet** , dass der Vorgang fehlgeschlagen ist.

* **Rückruf zur Implementierung**`onNotification(NotificationEvent event)`

* **Ereignis-Code**`OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **Das bedeutet** , dass der Wiedergabebereich aktualisiert wurde.

* **Rückruf zur Implementierung**`onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **Ereignis-Code**`PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **Das bedeutet** , dass eine neue Wiedergaberate auf dem Bildschirm sichtbar ist.

* **Rückruf zur Implementierung**`onRatePlaying(PlaybackRateEvent event)`

* **Ereignis-Code**`RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **Das bedeutet** , dass das Ratenattribut von MediaPlayer festgelegt wurde.

* **Rückruf zur Implementierung**`onRateSelected(PlaybackRateEvent event)`

* **Ereignis-Code**`RATE_SELECTED`

`PlayStartEventListener`

* **Das bedeutet** Die Wiedergabe wurde gestartet.

* **Rückruf zur Implementierung**`onPlayStart()`

* **Ereignis-Code**`PLAY_START`

`ProfileChangeEventListener`

* **Das bedeutet** , dass sich das aktuelle Profil des MediaPlayer geändert hat.

* **Rückruf zur Implementierung**`onProfileChanged(ProfileEvent event)`

* **Ereignis-Code**`PROFILE_CHANGED`

`ReservationReachedEventListener`

* **Das bedeutet** Wiedergabe erreichte eine Zeitschiene Reservierung.

* **Rückruf zur Implementierung**`onReservationReached(ReservationEvent event)`

* **Ereignis-Code**`RESERVATION_REACHED`

`SeekBeginEventListener`

* **Das bedeutet** , dass der Suchvorgang gestartet wurde.

* **Rückruf zur Implementierung**`onSeekBegin(SeekEvent event)`

* **Ereignis-Code**`SEEK_BEGIN`

`SeekEndEventListener`

* **Das bedeutet** Der Suchvorgang ist abgeschlossen.

* **Rückruf zur Implementierung**`onSeekEnd(SeekEvent event)`

* **Ereignis-Code**`SEEK_END`

`SeekPositionAdjustedEventListener`

* **Das bedeutet** , dass die Suchposition aufgrund interner Wiedergaberegeln oder externer Geschäftsregeln angepasst wurde.

* **Rückruf zur Implementierung**`onPositionAdjusted(SeekEvent event)`

* **Ereignis-Code**`SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **Das bedeutet** Die Größe des Mediums ist verfügbar.

* **Rückruf zur Implementierung**`onSizeAvailable(SizeAvailableEvent event)`

* **Ereignis-Code**`SIZE_AVAILABLE`

`StatusChangeEventListener`

* **Das bedeutet** , dass sich der MediaPlayer-Status geändert hat.

* **Rückruf zur Implementierung**`onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **Ereignis-Code**`STATUS_CHANGED`

`TimeChangeEventListener`

* **Das bedeutet** , dass sich der Abspielkopf verändert hat.

* **Rückruf zur Implementierung**`onTimeChanged(TimeChangeEvent event)`

* **Ereignis-Code**`TIME_CHANGED`

`TimedEventEventListener`

* **Das bedeutet** Der Vorgang ist abgeschlossen mit der für den Vorgang benötigten Zeit.

* **Rückruf zur Implementierung**`onTimedEvent(TimedEventEvent event)`

* **Ereignis-Code**`TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **Das bedeutet** , dass einem Element im Hintergrund neue zeitgesteuerte Metadaten hinzugefügt wurden.

* **Rückruf zur Implementierung**`onTimedMetadata(TimedMetadataEvent event)`

* **Ereignis-Code**`TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **Das bedeutet** , dass im Medienstream neue Metadaten mit Zeitüberschreitung erkannt wurden.

* **Rückruf zur Implementierung**`onTimedMetadata(TimedMetadataEvent event)`

* **Ereignis-Code**`TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **Das bedeutet** , dass die Zeitschiene geändert wurde. Anzeigen wurden möglicherweise der Zeitleiste hinzugefügt oder daraus entfernt.

* **Rückruf zur Implementierung**`onTimelineUpdated(TimelineEvent event)`

* **Ereignis-Code**`TIMELINE_UPDATED`