---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
title: Benutzerdefinierte Zeitbereichsoperationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Übersicht {#custom-time-range-operations-overview}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarkierungen. Benutzerdefinierte Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

Das Löschen und Ersetzen von Anzeigen wird mit benutzerdefinierten Markern implementiert, die verschiedene Arten von Zeitbereichen in einem VOD-Stream identifizieren: Markieren, Löschen und Ersetzen. Für jeden benutzerdefinierten Zeitraum können Sie zugehörige Vorgänge ausführen, einschließlich Löschen oder Ersetzen von Anzeigeninhalten.

Für das Löschen und Ersetzen von Anzeigen enthält TVSDK Folgendes: *benutzerdefinierter Zeitbereichsvorgang* Modi:

* MARK - Dispatches `AdBreak` -Ereignisse für die markierten Regionen. (Dies heißt `customAdMarker` in früheren Versionen von TVSDK.) In diesem Modus ist das Einfügen von Anzeigen nicht zulässig.

* DELETE - In diesem Modus verwendet das Programm die `TimeRangeCollection` -Klasse zum Definieren von Zeitbereichen für das Löschen von C3-Anzeigen. In diesem Modus ist das Einfügen von Anzeigen zulässig.
* ERSETZEN - In diesem Modus ersetzt die App eine `timeRange` mit einer Adobe Primetime-Anzeigenentscheidung `AdBreak`. Der Ersetzungsvorgang beginnt an der Stelle, an der das Löschen der C3-Anzeige erfolgt, und endet zum angegebenen Zeitpunkt (kürzer oder länger als der ursprüngliche Zeitraum).

TVSDK bietet eine `CustomRangesOpportunityGenerator` -Klasse, um Platzierungsmöglichkeiten für die Bereiche MARK und DELETE zu generieren. Für den ERSETZUNGSmodus generiert TVSDK zwei Platzierungsmöglichkeiten für jeden Zeitraum:

* Die `CustomRangeResolver` schafft Platzierungsmöglichkeiten für DELETE
* Die `AuditudeAdResolver` bietet Platzierungsmöglichkeiten für INSERT.
