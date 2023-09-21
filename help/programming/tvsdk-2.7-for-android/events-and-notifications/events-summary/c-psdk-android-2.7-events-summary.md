---
description: Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignisse wartet, die von TVSDK gesendet werden.
title: Übersicht über die Primetime-Player-Ereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# Übersicht über die Primetime-Player-Ereignisse {#primetime-player-events-summary-overview}

Ihre Anwendung kann die Aktivität in Ihrem Player und den sich ändernden Status des Players überwachen, indem sie auf die Ereignisse wartet, die von TVSDK gesendet werden.

## Veranstaltungen {#events}

TVSDK benachrichtigt Sie beim Auftreten von Ereignissen, auf die Ihre Anwendung reagieren muss. Jedes Ereignis entspricht einer Listener-Klasse mit einer Callback-Methode, die Sie implementieren müssen.

>[!TIP]
>
>Die Ereigniscodes sind die Konstanten der `MediaPlayerEvent` enum.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** Das bedeutet ** Die Wiedergabe der Werbeunterbrechung ist abgeschlossen.

* ** Rückruf zur Implementierung ** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* ** Ereigniscode ** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** Das bedeutet ** Während der Wiedergabe wurde eine Werbeunterbrechung übersprungen.

* ** Rückruf zur Implementierung ** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* ** Ereigniscode ** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** Das bedeutet ** Die Wiedergabe der Werbeunterbrechung wurde gestartet.

* ** Rückruf zur Implementierung ** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* ** Ereigniscode ** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** Das bedeutet ** Während der Wiedergabe wurde auf eine Anzeige geklickt.

* ** Rückruf zur Implementierung ** `onAdClicked(AdClickEvent event)`

* ** Ereigniscode ** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** Das bedeutet ** Die Wiedergabe der Anzeige ist abgeschlossen.

* ** Rückruf zur Implementierung ** `onAdCompleted(AdPlaybackEvent event)`

* ** Ereigniscode ** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** Das bedeutet ** Berichtsfortschritt während der Wiedergabe.

* ** Rückruf zur Implementierung ** `onAdProgress(AdPlaybackEvent event)`

* ** Ereigniscode ** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** Das bedeutet ** Die Primetime-Anzeigenentscheidung und die Auflösung sind abgeschlossen. Dieses Ereignis gilt nur für VOD-Inhalte.

* ** Rückruf zur Implementierung ** `onAdResolutionComplete()`

* ** Ereigniscode ** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** Das bedeutet ** Die Wiedergabe der Anzeige wurde gestartet.

* ** Rückruf zur Implementierung ** `onAdStarted(AdPlaybackEvent event)`

* ** Ereigniscode ** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** Bedeutung ** Ein neuer Audio-Track wurde erkannt.

* ** Rückruf zur Implementierung ** `onAudioUpdated(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** Bedeutung ** Der Player hat mit der Pufferung begonnen.

* ** Rückruf zur Implementierung ** `onBufferingBegin(BufferEvent event)`

* ** Ereigniscode ** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** Bedeutung ** Der Player hat die Pufferung beendet.

* ** Rückruf zur Implementierung ** `onBufferingEnd(BufferEvent event)`

* ** Ereigniscode ** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** bedeutet ** Der Puffer wird vorbereitet.

* ** Rückruf zur Implementierung ** `onBufferPrepared()`

* ** Ereigniscode ** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* ** Bedeutung ** Es wurde ein neuer Untertitelpfad erkannt.

* ** Rückruf zur Implementierung ** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** Das bedeutet ** Im Medien-Stream wurden neue DRM-Metadaten erkannt.

* ** Rückruf zur Implementierung ** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* ** Ereigniscode ** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** Das bedeutet ** Ein neues Medienplayer-Element wurde erstellt.

* ** Rückruf zur Implementierung ** `onItemCreated(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** Das bedeutet ** Für das aktuelle Element wurden neue Ladeinformationen erstellt.

* ** Rückruf zur Implementierung ** `onLoadComplete(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** Das bedeutet ** Es wurde ein neues Segment geladen.

* ** Rückruf zur Implementierung ** `onLoadInformation(LoadInformationEvent event)`

* ** Ereigniscode ** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** Das bedeutet ** Das Hauptmanifest oder die Wiedergabeliste wurde aktualisiert.

* ** Rückruf zur Implementierung ** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** bedeutet ** Der Vorgang ist fehlgeschlagen.

* ** Rückruf zur Implementierung ** `onNotification(NotificationEvent event)`

* ** Ereigniscode ** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** Das bedeutet ** Der Wiedergabefeld wurde aktualisiert.

* ** Rückruf zur Implementierung ** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* ** Ereigniscode ** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** Das bedeutet ** Eine neue Wiedergaberate ist auf dem Bildschirm sichtbar.

* ** Rückruf zur Implementierung ** `onRatePlaying(PlaybackRateEvent event)`

* ** Ereigniscode ** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** Bedeutung ** Das Ratenattribut des MediaPlayer wurde festgelegt.

* ** Rückruf zur Implementierung ** `onRateSelected(PlaybackRateEvent event)`

* ** Ereigniscode ** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** Bedeutung ** Die Wiedergabe wurde gestartet.

* ** Rückruf zur Implementierung ** `onPlayStart()`

* ** Ereigniscode ** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** Das bedeutet ** Das aktuelle Profil des MediaPlayer wurde geändert.

* ** Rückruf zur Implementierung ** `onProfileChanged(ProfileEvent event)`

* ** Ereigniscode ** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** Das bedeutet ** Die Wiedergabe hat eine Timeline-Reservierung erreicht.

* ** Rückruf zur Implementierung ** `onReservationReached(ReservationEvent event)`

* ** Ereigniscode ** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** Bedeutung ** Der Suchvorgang wurde gestartet.

* ** Rückruf zur Implementierung ** `onSeekBegin(SeekEvent event)`

* ** Ereigniscode ** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** Bedeutung ** Der Suchvorgang wurde abgeschlossen.

* ** Rückruf zur Implementierung ** `onSeekEnd(SeekEvent event)`

* ** Ereigniscode ** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** Das bedeutet ** Die Suchposition wurde aufgrund interner Wiedergaberegeln oder externer Geschäftsregeln angepasst.

* ** Rückruf zur Implementierung ** `onPositionAdjusted(SeekEvent event)`

* ** Ereigniscode ** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** Das bedeutet ** Die Größe des Mediums ist verfügbar.

* ** Rückruf zur Implementierung ** `onSizeAvailable(SizeAvailableEvent event)`

* ** Ereigniscode ** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** Das bedeutet ** Der MediaPlayer-Status hat sich geändert.

* ** Rückruf zur Implementierung ** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* ** Ereigniscode ** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** Bedeutung ** Die Abspielleiste hat sich geändert.

* ** Rückruf zur Implementierung ** `onTimeChanged(TimeChangeEvent event)`

* ** Ereigniscode ** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** Bedeutung ** Der Vorgang ist mit der für den Vorgang benötigten Zeit abgeschlossen.

* ** Rückruf zur Implementierung ** `onTimedEvent(TimedEventEvent event)`

* ** Ereigniscode ** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** Das bedeutet ** Ein Element im Hintergrund wurde um neue zeitgesteuerte Metadaten erweitert.

* ** Rückruf zur Implementierung ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Ereigniscode ** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* ** Das bedeutet ** Im Medien-Stream wurden neue zeitgesteuerte Metadaten erkannt.

* ** Rückruf zur Implementierung ** `onTimedMetadata(TimedMetadataEvent event)`

* ** Ereigniscode ** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** Bedeutung ** Die Zeitleiste wurde geändert. Anzeigen wurden der Timeline möglicherweise hinzugefügt oder aus ihr entfernt.

* ** Rückruf zur Implementierung ** `onTimelineUpdated(TimelineEvent event)`

* ** Ereigniscode ** `TIMELINE_UPDATED`
