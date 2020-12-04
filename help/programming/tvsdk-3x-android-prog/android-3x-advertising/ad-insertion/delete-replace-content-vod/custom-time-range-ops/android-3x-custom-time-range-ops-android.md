---
description: Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream-Markierungszeichen, Löschen und Ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.
seo-description: Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream-Markierungszeichen, Löschen und Ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.
seo-title: Benutzerdefinierte Zeitraumoperationen
title: Benutzerdefinierte Zeitraumoperationen
uuid: eadd4d8d-0e03-40ca-ae3b-eede82bf2df8
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Benutzerdefinierte Zeitraumoperationen {#custom-time-range-operations}

Die CustomRangeMetadata-Klasse identifiziert verschiedene Arten von Zeitbereichen in einem VOD-Stream: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK die folgenden *benutzerdefinierten Zeitraumoperationen*:

* **In früheren Versionen von TVSDK wurde** dieser Modus als benutzerdefinierte Anzeigenmarken bezeichnet. Der Modus markiert die Start- und Endzeiten für Anzeigen, die bereits im VOD-Stream platziert wurden. Wenn im Stream Zeitraummarken des Typs `MARK` vorhanden sind, wird eine anfängliche Platzierung von `Mode.MARK` von `CustomMarkerOpportunityGenerator` generiert und von `CustomRangeResolver` aufgelöst. Es werden keine Anzeigen eingefügt.

* **Bei** DELETEFs  `DELETE` Zeitbereichen  `placementInformation` wird eine Anfangstypdatei  `Mode.DELETE` erstellt und durch  `CustomRangeResolver`gelöst. `DeleteRangeTimelineOperation` definiert die Bereiche, die aus der Zeitleiste entfernt werden sollen, und TVSDK verwendet diese Operation  `removeByLocalTime` aus der Adobe Video Engine (AVE) API. Wenn DELETE- und Adobe Primetime-Anzeigenentscheidungsmetadaten vorhanden sind, werden die Bereiche zuerst gelöscht, dann löst `AuditudeResolver` Anzeigen mit dem typischen Adobe Primetime-Arbeitsablauf für Anzeigenentscheidungen.

* **** REPLACEFr  `REPLACE` Zeitbereiche  `placementInformations` werden zwei anfängliche Zeiträume erstellt, ein  `Mode.DELETE` und ein  `Mode.REPLACE`. `CustomRangeResolver` löscht zunächst die Zeiträume und  `AuditudeResolver` fügt dann Anzeigen des angegebenen Zeitraums  `replaceDuration` in die Zeitleiste ein. Wenn kein `replaceDuration` angegeben ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitraumoperationen stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

   Ein Stream kann über mehrere Inhaltsauflöser verfügen, die auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten basieren. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere anfängliche Möglichkeiten mit `CustomMarkerOpportunityGenerator`.
* Ein neuer Anzeigensignalisierungsmodus, `CUSTOM_RANGES`.

   Die Platzierung von Anzeigen basiert auf den Daten des Zeitraums aus einer externen Quelle, z. B. einer JSON-Datei.