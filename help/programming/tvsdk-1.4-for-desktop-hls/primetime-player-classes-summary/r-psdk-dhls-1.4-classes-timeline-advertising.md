---
description: Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.
title: Zeitleistenanzeigenklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Zeitleistenanzeigenklassen {#timeline-advertising-classes}

Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.

Package: [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)
Package: [com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| Name | Beschreibung |
|---|---|
| [Anzeige](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Klasse, die die Anzeigenabstraktion definiert und alle Anzeigeninformationen enthält. Sie wird durch eine eindeutige ID, eine Dauer und eine `MediaResource`. Die `MediaResource` enthält die URL, in der sich der tatsächliche Anzeigeninhalt befindet. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Klasse, die ein anzuzeigendes Asset darstellt. Klasse, die ein Anzeigen-Asset darstellt. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die irgendwann während der Wiedergabe wiedergegeben werden. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | Auflistung, die die Richtlinie zur Anzeigenwiedergabe definiert, die sich auf den Benutzer bezieht, der Anzeigen bei der Suche umgeht. |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | Zeitleistenelement, das mit der spezifischen Werbeunterbrechung verknüpft ist. |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | Auflistungsklasse für mögliche Richtlinien zum Zeitpunkt, zu dem eine Werbeunterbrechung als überwacht markiert werden soll. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, die verwendet werden können, um dem Benutzer zusätzliche Informationen bereitzustellen. |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | Auflistungsklasse für mögliche Richtlinien, in denen die Wiedergabe einer Werbeunterbrechung nach der Suche oder dem Trick-Play-Modus fortgesetzt werden soll. |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | Auflistungsklasse, die auflistet, wie der Player wiedergegeben wird, z. B. Suche oder normale Wiedergabe. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Schnittstelle, die Eigenschaften für definiert `AdPolicySelector` API-Aufrufe. Diese Eigenschaften bieten den Kontext für die Erzwingung jedes Anzeigenverhaltens. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | Eine Benutzeroberfläche zur Auswahl von Anzeigenrichtlinien zum Durchsetzen von Anzeigenverhalten. Anwendungen können dieser Schnittstelle entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtlinienauswahlklasse erweitern, um bestimmte Verhaltensweisen anzupassen. |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | Zeitleistenelement, das mit einer bestimmten Anzeige verknüpft ist. |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | Klasse, die die Primetime-Anzeigenauflösung im TVSDK-Prozess verarbeitet. |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | Auflistung aller vom TVSDK unterstützten Anzeigentypen. |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | Klasse. |
