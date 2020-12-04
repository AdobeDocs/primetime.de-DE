---
description: Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.
seo-description: Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.
seo-title: Übersicht zu Primetime-Player-Ereignissen
title: Übersicht zu Primetime-Player-Ereignissen
uuid: ed3be4c2-8df3-4d96-a30b-74c196262798
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Übersicht zu Primetime-Player-Ereignissen {#primetime-player-events-summary-overview}

Ihre Anwendung kann die Aktivität im Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignis überwacht, die von TVSDK gesendet werden.

## Ereignis {#events}

TVSDK benachrichtigt Sie, wenn Ereignis auftreten, auf die Ihre Anwendung reagieren muss. Jedes Ereignis entspricht einer Listener-Klasse mit einer Rückrufmethode, die Sie implementieren müssen.

>[!TIP]
>
>Die Ereignis-Codes sind die Konstanten der Enum `MediaPlayerEvent`.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Das bedeutet ** Die Wiedergabe der Werbeunterbrechung ist abgeschlossen.

* ** Rückruf zur Implementierung von ** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* ** Ereignis-Code ** `AD_BREAK_COMPLETE`

## AdBreakSkippingEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Das bedeutet ** Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen.

* ** Rückruf zur Implementierung von ** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* ** Ereignis-Code ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Das bedeutet ** Die Wiedergabe der Werbeunterbrechung hat begonnen.

* ** Rückruf zur Implementierung von ** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* ** Ereignis-Code ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Das bedeutet ** Während der Wiedergabe wurde auf eine Anzeige geklickt.

* ** Rückruf zur Implementierung von ** `onAdClicked(AdClickEvent event)`

* ** Ereignis-Code ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Das bedeutet ** Die Wiedergabe der Anzeige ist abgeschlossen.

* ** Rückruf zur Implementierung von ** `onAdCompleted(AdPlaybackEvent event)`

* ** Ereignis-Code ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Das bedeutet ** Berichte-Fortschritt während der Wiedergabe.

* ** Rückruf zur Implementierung von ** `onAdProgress(AdPlaybackEvent event)`

* ** Ereignis-Code ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Das bedeutet ** Die Primetime-Anzeigenentscheidung und die Auflösung sind abgeschlossen. Dieses Ereignis gilt nur für VOD-Inhalte.

* ** Rückruf zur Implementierung von ** `onAdResolutionComplete()`

* ** Ereignis-Code ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Das bedeutet ** Die Wiedergabe der Anzeige wurde gestartet.

* ** Rückruf zur Implementierung von ** `onAdStarted(AdPlaybackEvent event)`

* ** Ereignis-Code ** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Das bedeutet ** Eine neue Audiospur wurde erkannt.

* ** Rückruf zur Implementierung von ** `onAudioUpdated(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Das bedeutet ** Der Player hat mit der Pufferung begonnen.

* ** Rückruf zur Implementierung von ** `onBufferingBegin(BufferEvent event)`

* ** Ereignis-Code ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Das bedeutet ** Der Player hat die Pufferung beendet.

* ** Rückruf zur Implementierung von ** `onBufferingEnd(BufferEvent event)`

* ** Ereignis-Code ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** Das bedeutet ** Der Puffer wird vorbereitet.

* ** Rückruf zur Implementierung von ** `onBufferPrepared()`

* ** Ereignis-Code ** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Das bedeutet ** Eine neue Untertitelspur wurde erkannt.

* ** Rückruf zur Implementierung von ** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Das bedeutet ** Im Medienstream wurden neue DRM-Metadaten erkannt.

* ** Rückruf zur Implementierung von ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* ** Ereignis-Code ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Das bedeutet ** Es wurde ein neuer Medienplayer-Artikel erstellt.

* ** Rückruf zur Implementierung von ** `onItemCreated(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Das bedeutet ** Für das aktuelle Element wurden neue Ladeinformationen erstellt.

* ** Rückruf zur Implementierung von ** `onLoadComplete(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Das bedeutet ** Ein neues Segment wurde geladen.

* ** Rückruf zur Implementierung von ** `onLoadInformation(LoadInformationEvent event)`

* ** Ereignis-Code ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Das bedeutet ** Das Hauptmanifest oder die Wiedergabeliste wurde aktualisiert.

* ** Rückruf zur Implementierung von ** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** Das bedeutet ** Der Vorgang ist fehlgeschlagen.

* ** Rückruf zur Implementierung von ** `onNotification(NotificationEvent event)`

* ** Ereignis-Code ** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Das bedeutet ** Der Wiedergabebereich wurde aktualisiert.

* ** Rückruf zur Implementierung von ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* ** Ereignis-Code ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Das bedeutet ** Eine neue Wiedergabegeschwindigkeit ist auf dem Bildschirm sichtbar.

* ** Rückruf zur Implementierung von ** `onRatePlaying(PlaybackRateEvent event)`

* ** Ereignis-Code ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Das bedeutet ** Das Ratenattribut des MediaPlayers wurde eingestellt.

* ** Rückruf zur Implementierung von ** `onRateSelected(PlaybackRateEvent event)`

* ** Ereignis-Code ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Das bedeutet ** Die Wiedergabe wurde gestartet.

* ** Rückruf zur Implementierung von ** `onPlayStart()`

* ** Ereignis-Code ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Das bedeutet ** Das aktuelle Profil des MediaPlayers hat sich geändert.

* ** Rückruf zur Implementierung von ** `onProfileChanged(ProfileEvent event)`

* ** Ereignis-Code ** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Das bedeutet ** Die Wiedergabe hat eine zeitliche Reservierung erreicht.

* ** Rückruf zur Implementierung von ** `onReservationReached(ReservationEvent event)`

* ** Ereignis-Code ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Das bedeutet ** Der Suchvorgang wurde gestartet.

* ** Rückruf zur Implementierung von ** `onSeekBegin(SeekEvent event)`

* ** Ereignis-Code ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Das bedeutet ** Der Suchvorgang ist abgeschlossen.

* ** Rückruf zur Implementierung von ** `onSeekEnd(SeekEvent event)`

* ** Ereignis-Code ** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Das bedeutet ** Die Suchposition wurde aufgrund interner Wiedergaberegeln oder externer Geschäftsregeln angepasst.

* ** Rückruf zur Implementierung von ** `onPositionAdjusted(SeekEvent event)`

* ** Ereignis-Code ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Das bedeutet ** Die Größe des Mediums ist verfügbar.

* ** Rückruf zur Implementierung von ** `onSizeAvailable(SizeAvailableEvent event)`

* ** Ereignis-Code ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Das bedeutet ** Der MediaPlayer-Status wurde geändert.

* ** Rückruf zur Implementierung von ** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* ** Ereignis-Code ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Das bedeutet ** Die Abspielleiste hat sich geändert.

* ** Rückruf zur Implementierung von ** `onTimeChanged(TimeChangeEvent event)`

* ** Ereignis-Code ** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Das bedeutet ** Die Operation ist abgeschlossen mit der für die Operation benötigten Zeit.

* ** Rückruf zur Implementierung von ** `onTimedEvent(TimedEventEvent event)`

* ** Ereignis-Code ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Das bedeutet ** Eine neue zeitgesteuerte Metadaten wurde zu einem Element im Hintergrund hinzugefügt.

* ** Rückruf zur Implementierung von ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Ereignis-Code ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Das bedeutet ** Im Medienstream wurden neue zeitgesteuerte Metadaten erkannt.

* ** Rückruf zur Implementierung von ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Ereignis-Code ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Das bedeutet ** Die Zeitschiene wurde geändert. Anzeigen wurden möglicherweise der Zeitleiste hinzugefügt oder daraus entfernt.

* ** Rückruf zur Implementierung von ** `onTimelineUpdated(TimelineEvent event)`

* ** Ereignis-Code ** `TIMELINE_UPDATED`