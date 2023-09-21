---
description: Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream, das Markieren, Löschen und Ersetzen. Für jeden dieser benutzerdefinierten Zeitbereichstypen können Sie die entsprechenden Vorgänge ausführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.
title: Benutzerdefinierte Zeitbereichsoperationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Übersicht {#custom-time-range-operations}

Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitbereichstypen können Sie die entsprechenden Vorgänge ausführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK Folgendes *benutzerdefinierter Zeitbereichsvorgang* Modi:

* **MARK** Dieser Modus wurde in früheren Versionen von TVSDK als benutzerdefinierte Anzeigenmarkierungen bezeichnet. Der Modus markiert die Start- und Endzeiten für Anzeigen, die bereits in den VOD-Stream platziert wurden. Wenn Zeitbereichsmarkierungen vom Typ vorhanden sind `MARK` eine anfängliche Platzierung von `Mode.MARK` wird von `CustomMarkerOpportunityGenerator` und aufgelöst durch `CustomRangeResolver`. Es werden keine Anzeigen eingefügt.

* **DELETE** Für `DELETE` Zeitbereiche, eine `placementInformation` des Typs `Mode.DELETE` erstellt und aufgelöst von `CustomRangeResolver`. `DeleteRangeTimelineOperation` definiert die Bereiche, die aus der Timeline entfernt werden sollen, und TVSDK verwendet `removeByLocalTime` über die Adobe Video Engine (AVE)-API, um diesen Vorgang abzuschließen. Wenn es DELETE- und Adobe Primetime-Anzeigenentscheidungen-Metadaten gibt, werden die Bereiche zuerst gelöscht, dann wird die `AuditudeResolver` löst Anzeigen mithilfe des typischen Adobe Primetime-Arbeitsablaufs für Anzeigenentscheidungen auf.

* **ERSETZEN** Für `REPLACE` Zeitbereiche, zwei anfängliche `placementInformations` erstellt werden, eine `Mode.DELETE` und einem `Mode.REPLACE`. `CustomRangeResolver` löscht zunächst die Zeiträume und dann die `AuditudeResolver` fügt Anzeigen des angegebenen `replaceDuration` in die Zeitleiste ein. Wenn nicht `replaceDuration` festgelegt ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitbereichsvorgänge stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

  Ein Stream kann basierend auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten über mehrere Inhaltsauflöser verfügen. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere anfängliche Möglichkeiten mit `CustomMarkerOpportunityGenerator`.
* einen neuen Anzeigesignalmodus, `CUSTOM_RANGES`.

  Anzeigen werden basierend auf Zeitbereichsdaten aus einer externen Quelle platziert, z. B. einer JSON-Datei.
