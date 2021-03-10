---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
title: Benutzerdefinierte Zeitraumoperationen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# Benutzerdefinierte Zeitraumoperationen {#custom-time-range-operations}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarken. Benutzerspezifische Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als inhaltliche Zeiträume für Anzeigen. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

Das Löschen und Ersetzen von Anzeigen wird mit `TimeRange`-Elementen implementiert, die verschiedene Arten von Zeitbereichen in einem VOD-Stream identifizieren: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK die folgenden *benutzerdefinierten Zeitraumoperationen*:

* **MARK**
(Diese wurden in früheren Versionen von TVSDK als benutzerdefinierte Anzeigenmarken bezeichnet). Sie markieren die Start- und Endzeiten für Anzeigen, die bereits in den VOD-Stream platziert wurden. Wenn im Stream Zeitraummarkierungen vom Typ MARK vorhanden sind, wird eine anfängliche Platzierung von 
`Mode.MARK` vom  `CustomAdMarkersContentResolver`. Es werden keine Anzeigen eingefügt.

* ****
DELETEF- oder DELETE-Zeitbereiche, eine 
`placementInformation` vom Typ  `Mode.DELETE` wird von der entsprechenden Seite erstellt und aufgelöst  `DeleteContentResolver`. `ContentRemoval` ist eine neue Version,  `timelineOperation` die die Bereiche definiert, die aus der Zeitleiste entfernt werden sollen. TVSDK verwendet `removeByLocalTime` aus der Adobe Video Engine (AVE) API, um diesen Vorgang zu erleichtern. Wenn es DELETE- und Adobe Primetime-Anzeigenentscheidungsmetadaten (früher Auditude genannt) gibt, werden die Bereiche zuerst gelöscht, dann löst `AuditudeResolver` Anzeigen mit dem normalen Adobe Primetime-Anzeigenbestimmungsarbeitsablauf.

* **REPLACEF-**
oder REPLACE-Zeitbereiche, zwei anfängliche 
`placementInformations` erstellt werden, eins  `Mode.DELETE` und eins  `Mode.REPLACE`. Mit `DeleteContentResolver` werden die Zeitbereiche zuerst gelöscht und mit `AuditudeResolver` werden Anzeigen des angegebenen `replaceDuration` in die Zeitleiste eingefügt. Wenn kein `replaceDuration` angegeben ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitraumoperationen stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

   Ein Stream kann über mehrere Inhaltsauflöser verfügen, die auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten basieren. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere anfängliche `PlacementInformations` Die `DefaultMediaPlayer`-Variable erstellt eine Liste von anfänglich `PlacementInformations`, basierend auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten, die durch die `MediaPlayerClient` aufgelöst werden sollen.

* Neuer Anzeigensignalisierungsmodus: Benutzerdefinierte Zeitbereiche

   Die Platzierung von Anzeigen basiert auf den Daten des Zeitraums aus einer externen Quelle (z. B. einer JSON-Datei).