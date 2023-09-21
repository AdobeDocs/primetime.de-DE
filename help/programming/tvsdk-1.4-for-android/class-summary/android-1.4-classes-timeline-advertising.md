---
description: Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.
title: Zeitleistenanzeigenklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Zeitleistenanzeigenklassen{#timeline-advertising-classes}

Diese Klassen liefern Informationen über Anzeigen, die innerhalb einer Timeline auftreten.

Package: [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Package: [com.adobe.mediacore.timeline.advertising.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Name | Beschreibung |
|--- |--- |
| [Anzeige](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Klasse, die die Anzeigenabstraktion definiert und alle Anzeigeninformationen enthält. Sie wird durch eine eindeutige ID, eine Dauer und eine `MediaResource`. Die `MediaResource` enthält die URL, in der sich der tatsächliche Anzeigeninhalt befindet. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Klasse, die ein anzuzeigendes Asset darstellt. Klasse, die ein Anzeigen-Asset darstellt. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Klasse, die eine einheitliche Ansicht für mehrere Anzeigen bietet, die irgendwann während der Wiedergabe wiedergegeben werden. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | Vorgangsklasse für Werbeunterbrechungen. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | Auflistung, die die Richtlinie zur Anzeigenwiedergabe definiert, die sich auf den Benutzer bezieht, der Anzeigen bei der Suche umgeht. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Klasse, die eine mit einem Asset verknüpfte Klickinstanz darstellt. Diese Instanz enthält Informationen zur Clickthrough-URL und zum Titel, die verwendet werden können, um dem Benutzer zusätzliche Informationen bereitzustellen. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Schnittstelle, die Eigenschaften für AdPolicySelector-API-Aufrufe definiert. Diese Eigenschaften bieten den Kontext für die Erzwingung jedes Anzeigenverhaltens. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | Eine Benutzeroberfläche zur Auswahl von Anzeigenrichtlinien zum Durchsetzen von Anzeigenverhalten. Anwendungen können dieser Schnittstelle entsprechen, indem sie alle erforderlichen Methoden implementieren oder die vorhandene Standard-Richtlinienauswahlklasse erweitern, um bestimmte Verhaltensweisen anzupassen. |
| `auditude.AuditudeAdProvider` | Veraltet. Verwenden Sie AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Klasse, die die Primetime-Anzeigenauflösung im Phrase-Prozess verarbeitet. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Klasse, die die ContentTracker-Schnittstelle implementiert und Primetime-Anzeigenverfolgungsereignisse definiert. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Klasse, die den Teil mit Anzeigenauflösung im Phrase-Prozess verarbeitet. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Schnittstelle, die das Protokoll definiert, das Sie implementieren müssen, wenn Sie ein Anzeigen-Tracking-Modul erstellen möchten, das zur Integration in die Bibliothek oder einen benutzerdefinierten Anzeigen-Tracker entwickelt wurde. Für diese Schnittstelle müssen Sie festlegen, wie Ereignisse des Anzeigenfortschritts dem Remote-Anzeigen-Tracking-System gemeldet werden. |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Klasse, die eine Platzierungsinformationen-Anfrage abstrahiert. An jede aufgelöste Anzeige muss eine Platzierungsinformationen angehängt sein. Die Platzierungsinformationen beschreiben, wo die Anzeige in der Timeline platziert werden soll. Er enthält Informationen wie: <ul><li>Platzierung (in ms) </li><li>Platzierungstyp (Pre-Roll, Mid-Roll oder Post-Roll) </li><li>Dauer des Hauptinhaltsabschnitts, der ersetzt werden soll</li></ul> |
