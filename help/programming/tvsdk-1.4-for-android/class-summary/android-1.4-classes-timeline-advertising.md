---
description: Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.
seo-description: Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.
seo-title: Zeitschienenwerbungskurse
title: Zeitschienenwerbungskurse
uuid: 4e6ca9fb-9e68-4625-a24b-386a50333862
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Zeitschienenwerbungskurse{#timeline-advertising-classes}

Diese Klassen bieten Informationen zu Anzeigen, die innerhalb einer Zeitleiste auftreten.

Paket: [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Paket: [com.adobe.mediacore.timeline.advertising.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Name | Beschreibung |
|--- |--- |
| [Anzeige](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Klasse, die die Abstraktion der Anzeige definiert und alle Anzeigeninformationen enthält. Er wird durch eine eindeutige ID, eine Dauer und eine `MediaResource`Variable definiert. Die `MediaResource` enthält die URL, in der sich der tatsächliche Anzeigeninhalt befindet. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Klasse, die ein anzuzeigendes Asset darstellt. Klasse, die ein Anzeigenasset darstellt. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die zu einem bestimmten Zeitpunkt während der Wiedergabe wiedergegeben werden. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | Platzierungsklasse für Werbeunterbrechungen. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | Auflistung, die die Richtlinie zur Anzeigenwiedergabe definiert, die sich auf den Benutzer bezieht, der Anzeigen bei der Suche umgeht. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, mit denen dem Benutzer zusätzliche Informationen bereitgestellt werden können. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Schnittstelle, die Eigenschaften für AdPolicySelector-API-Aufrufe definiert. Diese Eigenschaften bieten den Kontext zum Erzwingen jedes Anzeigenverhaltens. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | Eine Oberfläche zur Auswahl von Anzeigenrichtlinien zum Erzwingen von Anzeigenverhalten. Anwendungen können dieser Schnittstelle entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtliniensatzklasse erweitern, um bestimmte Verhaltensweisen anzupassen. |
| `auditude.AuditudeAdProvider` | Veraltet. Verwenden Sie AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Klasse, die die Primetime-und die Auflösung im Phrase-Prozess verarbeitet. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Klasse, die die ContentTracker-Schnittstelle implementiert und Primetime-Ereignis zur Anzeigenverfolgung definiert. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Klasse, die den Teil mit der Anzeigenauflösung im Phrase-Prozess verarbeitet. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Schnittstelle, die das Protokoll definiert, das Sie implementieren müssen, wenn Sie ein Anzeigenverfolgungsmodul erstellen möchten, das in die Bibliothek oder einen benutzerdefinierten Anzeigentracker integriert werden soll. Für diese Oberfläche müssen Sie festlegen, wie Ereignis mit Anzeigenfortschritten dem Remote-Anzeigenverfolgungssystem gemeldet werden. |
| [Platzierungsinformationen](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Klasse, die eine Platzierungsinformationen-Anforderung abstrahiert. Jeder gelösten Anzeige muss eine Platzierungsinformationen beigefügt sein. Die Platzierungsinformationen beschreiben, wo die Anzeige auf der Zeitschiene platziert werden soll. Er enthält Informationen wie: <ul><li>Platzierungsposition (in ms) </li><li>Platzierungstyp (Pre-Roll, Mid-Roll oder Post-Roll) </li><li>Dauer des Hauptinhaltsblocks, der ersetzt werden soll</li></ul> |
