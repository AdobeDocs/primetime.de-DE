---
description: TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.
title: Benutzerdefinierte Zeitbereichsoperationen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Benutzerdefinierte Zeitbereichsoperationen {#custom-time-range-operations}

TVSDK unterstützt das programmatische Löschen und Ersetzen von Anzeigeninhalten in VOD-Streams.

Die Funktion zum Löschen und Ersetzen erweitert die Funktion für benutzerdefinierte Anzeigenmarkierungen. Benutzerdefinierte Anzeigenmarkierungen markieren Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume. Neben der Kennzeichnung dieser Zeiträume können Sie auch Zeitbereiche löschen und ersetzen.

Das Löschen und Ersetzen von Anzeigen wird mit implementiert. `TimeRange` Elemente, die verschiedene Arten von Zeitbereichen in einem VOD-Stream identifizieren: markieren, löschen und ersetzen. Für jeden dieser benutzerdefinierten Zeitbereichstypen können Sie die entsprechenden Vorgänge ausführen, einschließlich Löschen und Ersetzen von Anzeigeninhalten.

Für das Löschen und Ersetzen von Anzeigen verwendet TVSDK Folgendes *benutzerdefinierter Zeitbereichsvorgang* Modi:

* **MARK**
(Diese wurden in früheren Versionen von TVSDK als benutzerdefinierte Anzeigenmarkierungen bezeichnet.) Sie markieren die Start- und Endzeiten für Anzeigen, die bereits in den VOD-Stream platziert wurden. Wenn Zeitbereichsmarkierungen des Typs MARK im Stream vorhanden sind, wird eine erste Platzierung von `Mode.MARK` wird von der `CustomAdMarkersContentResolver`. Es werden keine Anzeigen eingefügt.

* **DELETE**
Für DELETE-Zeiträume wird eine erste `placementInformation` des Typs `Mode.DELETE` erstellt und aufgelöst durch die entsprechende `DeleteContentResolver`. `ContentRemoval` ist neu `timelineOperation` definiert die Bereiche, die aus der Timeline entfernt werden sollen. TVSDK verwendet `removeByLocalTime` über die Adobe Video Engine (AVE)-API, um diesen Vorgang zu erleichtern. Wenn es DELETE- und Adobe Primetime-Anzeigenentscheidungen (ehemals Auditude)-Metadaten gibt, werden die Bereiche zuerst gelöscht, dann wird die `AuditudeResolver` löst Anzeigen mithilfe des normalen Adobe Primetime-Arbeitsablaufs für Anzeigenentscheidungen auf.

* **ERSETZEN**
Für ERSETZUNGS-Zeiträume werden zwei anfängliche `placementInformations` erstellt werden, eine `Mode.DELETE` und einem `Mode.REPLACE`. Die `DeleteContentResolver` löscht zunächst die Zeiträume und dann die `AuditudeResolver` fügt Anzeigen des angegebenen `replaceDuration` in die Zeitleiste ein. Wenn nicht `replaceDuration` festgelegt ist, bestimmt der Server, was eingefügt werden soll.

Zur Unterstützung dieser benutzerdefinierten Zeitbereichsvorgänge stellt TVSDK Folgendes bereit:

* Mehrere Inhaltsauflöser

  Ein Stream kann basierend auf dem Anzeigensignalisierungsmodus und den Anzeigenmetadaten über mehrere Inhaltsauflöser verfügen. Das Verhalten ändert sich mit verschiedenen Kombinationen von Anzeigensignalisierungsmodi und Anzeigenmetadaten.
* Mehrere Initialisierungen `PlacementInformations` Die `DefaultMediaPlayer` erstellt eine Liste der ersten `PlacementInformations` basierend auf dem Anzeigenanzeigemodus und den Anzeigenmetadaten, die vom `MediaPlayerClient`.

* Neuer Anzeigesignaturmodus: Benutzerdefinierte Zeitbereiche

  Anzeigen werden basierend auf Zeitbereichsdaten aus einer externen Quelle platziert (z. B. einer JSON-Datei).
