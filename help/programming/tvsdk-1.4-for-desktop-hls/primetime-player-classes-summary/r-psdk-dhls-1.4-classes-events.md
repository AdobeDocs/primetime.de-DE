---
description: Diese Klassen beschreiben Ereignis, die das TVSDK als Reaktion auf verschiedene Aktivitäten an Ihren Medienplayer sendet.
seo-description: Diese Klassen beschreiben Ereignis, die das TVSDK als Reaktion auf verschiedene Aktivitäten an Ihren Medienplayer sendet.
seo-title: Ereignis-Klassen
title: Ereignis-Klassen
uuid: 5e63d43c-6112-4958-b8cd-ccf123affd08
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# Ereignisses-Klassen {#events-classes}

Diese Klassen beschreiben Ereignis, die das TVSDK als Reaktion auf verschiedene Aktivitäten an Ihren Medienplayer sendet.

Paket: [com.adobe.mediacore.Ereignisses](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/package-detail.html)

| Name | Bedeutung |
|---|---|
| [AdBreakPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html) | Klasse. Eine Werbeunterbrechung wurde gestartet oder abgeschlossen. |
| [AdClickEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html) | Klasse. Der Benutzer klickte auf eine Anzeige. |
| [AdPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html) | Klasse. Der Spieler spielte eine Anzeige. |
| [BufferEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html) | Klasse. Der Player hat die Pufferung gestartet oder beendet. |
| [CustomAdEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/CustomAdEvent.html) | Klasse. Der Player zeigt den Status zum Laden benutzerdefinierter Anzeigen an und kann Anzeigen ignorieren, die Fehler aufweisen oder zu lange zum Laden benötigen. |
| [DRMMetadataInfoEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html) | Klasse. Neue DRM-Metadaten werden mit dem aktuellen Element verknüpft. |
| [LoadInformationEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/LoadInformationEvent.html) | Klasse. Downloadinformationen stehen für den aktuellen Medienstream zur Verfügung, der abgespielt wird. |
| [MediaPlayerItemEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html) | Klasse. Ein Medienplayer-Element wurde erstellt. |
| [MediaPlayerItemLoaderEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemLoaderEvent.html) | Klasse. Ein Ladevorgang wurde abgeschlossen. Dispatched by `MediaPlayerItemLoader`, um seine Kunden zu benachrichtigen. |
| [MediaPlayerStatusChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html) | Klasse. Der Status des Medienplayers wurde geändert. |
| [MediaPlayerViewEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerViewEvent.html) | Klasse. Auf `MediaPlayerView` wurde geklickt. |
| [PlaybackRateEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html) | Klasse. Die Wiedergaberate des Medienplayers ändert sich. |
| [profileEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html) | Klasse. Der Algorithmus zum Wechseln der adaptiven Bitrate des Medienplayers ist aufgrund von Netzwerk- oder Maschinenbedingungen auf ein anderes Profil umgestellt worden. |
| [SeekEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html) | Klasse. Der Player hat mit der Suche begonnen oder der Suchvorgang abgeschlossen. |
| [SizeAvailableEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SizeAvailableEvent.html) | Klasse. Die Videogröße ist verfügbar. |
| [TimeChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html) | Klasse. Der Status des Medienplayers wurde geändert. |
| [TimedMetadataEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html) | Klasse. Zeitgesteuerte Metadaten werden vom Opportunitätsdetektor verarbeitet. |
| [TimelineEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html) | Klasse. Die Zeitleiste des Medienplayers wurde geändert. |