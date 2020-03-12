---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
seo-title: Benutzerdefinierte Zeitraumoperationen
title: Benutzerdefinierte Zeitraumoperationen
uuid: e04af786-8dac-41a6-8406-f2ca04f612a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Benutzerdefinierte Zeitraumoperationen {#custom-time-range-operations}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarken. Benutzerspezifische Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als inhaltliche Zeiträume für Anzeigen. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

Das Löschen und Ersetzen von Anzeigen wird mit `TimeRange` Elementen implementiert, die verschiedene Arten von Zeitbereichen in einem VOD-Stream identifizieren: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitraumtypen können Sie entsprechende Vorgänge durchführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK die folgenden *benutzerdefinierten Zeitraumoperationen* :

* **MARK**(Diese wurden in früheren Versionen von TVSDK als benutzerdefinierte Anzeigenmarken bezeichnet). Sie markieren die Start- und Endzeiten für Anzeigen, die bereits in den VOD-Stream platziert wurden. Wenn der Stream Zeitraummarken vom Typ MARK enthält, `Mode.MARK` wird eine anfängliche Platzierung von erzeugt und durch die `CustomAdMarkersContentResolver`aufgelöst. Es werden keine Anzeigen eingefügt.

* **LÖSCHEN** Für DELETE-Zeiträume wird ein Anfangstyp `placementInformation` des Typs erstellt `Mode.DELETE` und durch den entsprechenden aufgelöst `DeleteContentResolver`. `ContentRemoval` ist eine neue Funktion, `timelineOperation` die die Bereiche definiert, die aus der Zeitleiste entfernt werden sollen. TVSDK verwendet `removeByLocalTime` die API der Adobe Video Engine (AVE), um diesen Vorgang zu erleichtern. Wenn es DELETE-Bereiche und Adobe Primetime-Anzeigenentscheidungsmetadaten (früher Auditude genannt) gibt, werden die Bereiche zuerst gelöscht, dann löst die `AuditudeResolver` Anzeige mit dem normalen Adobe Primetime-Anzeigenbestimmungsarbeitsablauf ab.

* **ERSETZEN** Für ERSETZUNGSzeitbereiche `placementInformations` werden zwei Anfangsbereiche erstellt, ein `Mode.DELETE` und ein `Mode.REPLACE`. Der `DeleteContentResolver` Zeitbereich wird zuerst gelöscht, und dann werden Anzeigen des angegebenen `AuditudeResolver` Zeitraums `replaceDuration` in die Zeitleiste eingefügt. Wenn kein Wert angegeben `replaceDuration` ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitraumoperationen stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

   Ein Stream kann über mehrere Inhaltsauflöser verfügen, die auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten basieren. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere erste `PlacementInformations` Die `DefaultMediaPlayer` Erstellung einer Liste der Initialen `PlacementInformations` basiert auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten, die vom `MediaPlayerClient`.

* Neuer Anzeigensignalisierungsmodus: Benutzerdefinierte Zeitbereiche

   Die Platzierung von Anzeigen basiert auf den Daten des Zeitraums aus einer externen Quelle (z. B. einer JSON-Datei).