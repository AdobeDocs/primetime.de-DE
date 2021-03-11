---
description: Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.
title: Zeitschienenwerbungskurse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Zeitschienenwerbungsklassen {#timeline-advertising-classes}

Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.

Paket: [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)
Paket: [com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| Name | Beschreibung |
|---|---|
| [Anzeige](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Klasse, die die Abstraktion der Anzeige definiert und alle Anzeigeninformationen enthält. Er wird durch eine eindeutige ID, eine Dauer und ein `MediaResource` definiert. Das `MediaResource` enthält die URL, in der sich der tatsächliche Anzeigeninhalt befindet. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Klasse, die ein anzuzeigendes Asset darstellt. Klasse, die ein Anzeigenasset darstellt. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die zu einem bestimmten Zeitpunkt während der Wiedergabe wiedergegeben werden. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | Auflistung, die die Richtlinie zur Anzeigenwiedergabe definiert, die sich auf den Benutzer bezieht, der Anzeigen bei der Suche umgeht. |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | Zeitschienenelement, das mit der jeweiligen Werbeunterbrechung verknüpft ist. |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | Auflistung-Klasse für mögliche Richtlinien zum Zeitpunkt, zu dem eine Werbeunterbrechung als überwacht gekennzeichnet wird. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, mit denen dem Benutzer zusätzliche Informationen bereitgestellt werden können. |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | Auflistung-Klasse für mögliche Richtlinien, wo die Wiedergabe einer Werbeunterbrechung nach der Suche oder dem Trick-Play-Modus fortgesetzt werden soll. |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | Auflistung-Klasse, die Listen für die Wiedergabe des Players, wie z. B. Suche oder normale Wiedergabe, angibt. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Schnittstelle, die Eigenschaften für `AdPolicySelector`-API-Aufrufe definiert. Diese Eigenschaften bieten den Kontext zum Erzwingen jedes Anzeigenverhaltens. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Eine Oberfläche zur Auswahl von Anzeigenrichtlinien zum Erzwingen von Anzeigenverhalten. Anwendungen können dieser Schnittstelle entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtliniensatzklasse erweitern, um bestimmte Verhaltensweisen anzupassen. |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | Zeitschienenelement, das einer bestimmten Anzeige zugeordnet ist. |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | Klasse, die die Primetime-und die Auflösung im TVSDK-Prozess verarbeitet. |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | Auflistung aller vom TVSDK unterstützten Anzeigentypen. |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | Klasse. |

