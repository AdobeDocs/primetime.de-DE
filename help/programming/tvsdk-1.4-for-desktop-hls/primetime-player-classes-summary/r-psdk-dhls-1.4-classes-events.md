---
description: Diese Klassen beschreiben Ereignisse, die das TVSDK als Reaktion auf verschiedene Aktivitäten an Ihren Medienplayer sendet.
title: Ereignisklassen
exl-id: a349984a-5e47-4895-a56f-ef25eb372c79
source-git-commit: 776d3d1668f063f1595bd3ecb53603171905014a
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Ereignisklassen {#events-classes}

Diese Klassen beschreiben Ereignisse, die das TVSDK als Reaktion auf verschiedene Aktivitäten an Ihren Medienplayer sendet.

Package: [com.adobe.mediacore.events](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/package-detail.html)

| Name | Bedeutung |
|---|---|
| [AdBreakPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html) | Klasse. Eine Werbeunterbrechung wurde gestartet oder abgeschlossen. |
| [AdClickEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html) | Klasse. Der Benutzer klickte auf eine Anzeige. |
| [AdPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html) | Klasse. Der Player hat eine Anzeige wiedergegeben. |
| [BufferEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html) | Klasse. Der Player hat die Pufferung gestartet oder beendet. |
| [CustomAdEvent](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-1-4-for-desktop-hls/advertising/custom-ads/r-psdk-dhls-1.4-custom-ad-events.html?lang=en) | Klasse. Der Player zeigt den Status des Ladens benutzerdefinierter Anzeigen an und kann Anzeigen ignorieren, die Fehler aufweisen oder zu lange zum Laden benötigen. |
| [DRMMetadataInfoEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html) | Klasse. Neue DRM-Metadaten sind mit dem aktuellen Element verknüpft. |
| [LoadInformationEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/LoadInformationEvent.html) | Klasse. Download-Informationen sind für den aktuellen Medien-Stream verfügbar, der abgespielt wird. |
| [MediaPlayerItemEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html) | Klasse. Ein Medienplayer-Element wurde erstellt. |
| [MediaPlayerItemLoaderEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemLoaderEvent.html) | Klasse. Ein Ladevorgang wurde abgeschlossen. Versendet von `MediaPlayerItemLoader` ihre Kunden zu benachrichtigen. |
| [MediaPlayerStatusChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html) | Klasse. Der Medienplayer-Status wurde geändert. |
| [MediaPlayerViewEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerViewEvent.html) | Klasse. Die `MediaPlayerView` auf klicken. |
| [PlaybackRateEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html) | Klasse. Die Wiedergaberate des Medienplayers ändert sich. |
| [ProfileEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html) | Klasse. Der Algorithmus zum Wechseln der adaptiven Bitrate des Medienplayers ist aufgrund von Netzwerk- oder Maschinenbedingungen zu einem anderen Profil gewechselt. |
| [SeekEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html) | Klasse. Der Player startete die Suche oder der Suchvorgang wurde abgeschlossen. |
| [SizeAvailableEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SizeAvailableEvent.html) | Klasse. Die Videogröße ist verfügbar. |
| [TimeChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html) | Klasse. Der Status des Medienplayers wurde geändert. |
| [TimedMetadataEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html) | Klasse. Zeitgesteuerte Metadaten werden vom Opportunity-Detektor verarbeitet. |
| [TimelineEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html) | Klasse. Die Zeitleiste des Medienplayers wurde geändert. |
