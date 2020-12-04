---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-title: Benutzerdefinierte Zeitraumoperationen
title: Benutzerdefinierte Zeitraumoperationen
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Übersicht {#custom-time-range-operations-overview}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarken. Benutzerspezifische Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als inhaltliche Zeiträume für Anzeigen. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

Das Löschen und Ersetzen von Anzeigen werden mit benutzerdefinierten Markern implementiert, die verschiedene Arten von Zeitbereichen in einem VOD-Stream identifizieren: markieren, löschen und ersetzen. Für jeden benutzerdefinierten Zeitraum können Sie zugehörige Vorgänge durchführen, einschließlich Löschen oder Ersetzen von Anzeigeninhalten.

Für das Löschen und Ersetzen von Anzeigen enthält TVSDK die folgenden Modi *benutzerdefinierter Zeitbereich*:

* MARK - Dispatches `AdBreak` Ereignis für die markierten Bereiche. (Dies wurde in früheren Versionen von TVSDK als `customAdMarker` bezeichnet.) In diesem Modus ist das Einfügen von Anzeigen nicht zulässig.

* DELETE - In diesem Modus verwendet die App die `TimeRangeCollection`-Klasse, um Zeitbereiche für die Löschung von C3-Anzeigen zu definieren. In diesem Modus ist das Einfügen von Anzeigen zulässig.
* ERSETZEN - In diesem Modus ersetzt die App ein `timeRange` durch eine Adobe Primetime-Anzeigenentscheidung `AdBreak`. Der Vorgang &quot;Ersetzen&quot;wird in Beginn ausgeführt, in denen der Löschvorgang der C3-Anzeige stattfindet und zum angegebenen Zeitpunkt endet (kürzer oder länger als der ursprüngliche Zeitraum).

TVSDK bietet eine `CustomRangesOpportunityGenerator`-Klasse zum Generieren von Platzierungsmöglichkeiten für die Bereiche MARK und DELETE. Für den REPLACE-Modus generiert TVSDK zwei Platzierungsmöglichkeiten für jeden Zeitraum:

* Das `CustomRangeResolver` generiert Platzierungsmöglichkeiten für DELETE
* Das `AuditudeAdResolver` generiert Platzierungsmöglichkeiten für INSERT.