---
description: Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream-Markierungszeichen, Löschen und Ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.
seo-description: Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream-Markierungszeichen, Löschen und Ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.
seo-title: Benutzerdefinierte Zeitraumoperationen
title: Benutzerdefinierte Zeitraumoperationen
uuid: e9c6a135-124e-44d4-adf2-dc9d671e2483
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Übersicht {#custom-time-range-operations}

Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK die folgenden *benutzerdefinierten Zeitraumoperationen* :

* **MARK** Dieser Modus wurde in früheren Versionen von TVSDK als benutzerdefinierte Anzeigenmarken bezeichnet. Der Modus markiert die Start- und Endzeiten für Anzeigen, die bereits im VOD-Stream platziert wurden. Wenn `MARK` im Stream Zeitraummarken vom Typ vorhanden sind, `Mode.MARK` wird eine anfängliche Platzierung von erzeugt `CustomMarkerOpportunityGenerator` und von aufgelöst `CustomRangeResolver`. Es werden keine Anzeigen eingefügt.

* **LÖSCHEN** Für `DELETE` Zeiträume wird eine Anfangsart `placementInformation` des Typs erstellt `Mode.DELETE` und durch gelöst `CustomRangeResolver`. `DeleteRangeTimelineOperation` definiert die Bereiche, die aus der Zeitleiste entfernt werden sollen, und TVSDK verwendet diese Operation `removeByLocalTime` aus der Adobe Video Engine (AVE)-API. Wenn es DELETE-Bereiche und Adobe Primetime-Anzeigenentscheidungsmetadaten gibt, werden die Bereiche zuerst gelöscht, dann löst die `AuditudeResolver` Anzeige mithilfe des typischen Adobe Primetime-Arbeitsablaufs für Anzeigenentscheidungen.

* **ERSETZEN** Für `REPLACE` Zeiträume werden zwei erste `placementInformations` erstellt, ein `Mode.DELETE` und ein `Mode.REPLACE`. `CustomRangeResolver` löscht zunächst die Zeiträume und fügt dann Anzeigen des angegebenen Zeitraums `AuditudeResolver` `replaceDuration` in die Zeitleiste ein. Wenn kein Wert angegeben `replaceDuration` ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitraumoperationen stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

   Ein Stream kann über mehrere Inhaltsauflöser verfügen, die auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten basieren. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere anfängliche Möglichkeiten mit `CustomMarkerOpportunityGenerator`.
* Ein neuer Anzeigensignalisierungsmodus `CUSTOM_RANGES`.

   Die Platzierung von Anzeigen basiert auf den Daten des Zeitraums aus einer externen Quelle, z. B. einer JSON-Datei.

