---
description: Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
seo-description: Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
seo-title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Änderungen an der API zum Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-api-changes}

Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.

* `AdSignalingMode` Der  `CUSTOM_RANGES` Signalmodus wurde hinzugefügt.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Wird eingestellt,  `AdSignalingMode.CUSTOM_RANGES` wenn die Ersatzbereiche in den Metadaten enthalten sind.

* `PlacementType` Hinzugefügter  `CUSTOM_RANGE` Typ.

* `PlacementMode`

   * Der Modus `DELETE` wurde hinzugefügt.
   * `MARK`-Modus hinzugefügt
   * Modus `FreeReplace` hinzugefügt - Dieser Modus hat eine Dauer, ist jedoch eine reine Einfügung

* `TimeRange` Keine  `final` Klasse mehr

* `ReplaceTimeRange()`-Methode hinzugefügt

   Erweitert `TimeRange` um eine `replacementDuration`-Eigenschaft. Für die Fälle MARK und DELETE ist `replacementDuration` 0.

* `TimeRangeCollection`

   * Die Dienstprogrammfunktion `toReplaceMetadata()` wurde hinzugefügt, um `timeRanges` zu extrahieren.

   * Geändert für die Verwendung mit `DELETE` und `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`,  `METADATA_KEY_CUSTOM_DELETE_RANGES`,  `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * `createCustomTimeRangesFrom()` - Erstellt Metadaten für MARK/DELETE/REPLACE-Anwendungsfälle aus der JSON-Datei.
   * Entfernt `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * `CUSTOM_DELETE_RANGES_METADATA_KEY` hinzugefügt
   * `CUSTOM_REPLACE_RANGES_METADATA_KEY` hinzugefügt
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (nicht geändert)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * `CustomRangesOpportunityGenerator` hinzugefügt, wenn die Metadaten benutzerdefinierte Bereiche enthalten
   * `doRetrieveResolvers()`

      * hinzufügen `CustomRangeResolver` für den Fall, dass benutzerdefinierte Bereiche für DELETE und ERSETZEN in den Metadaten vorhanden sind
      * `CustomAdMarkerResolver` vor `AuditudeResolver` verschoben


* `CustomRangeOpportunityGenerator` hinzugefügt

   * `doUpdate()` Leer lassen - kein Update, VOD
   * `doProcess()` Erstellt eine neue Platzierung eines neuen Typs  `Placement.Delete_Range`

   * `CustomRangeOppotunityGenerator` wurde oben in der Generatoren-Liste in `DefaultContentFactory` hinzugefügt, sodass Löschbereiche vor Anzeigeneinfügungen verarbeitet werden.

   * `createCustomRangeOpportunities` hinzugefügt, um alle Möglichkeiten zu erstellen

      MARK - Eine Gelegenheit für jeden gültigen Markierungsbereich von `PlacementType.CUSTOM_RANGE` und `PlacementMode.MARK`

      DELETE - Eine Möglichkeit für jeden gültigen Löschbereich von `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`

      ERSETZEN - Zwei Möglichkeiten für jeden gültigen Ersatzbereich:

      1. Eine Löschbereichsmöglichkeit von `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`.

      1. Eine Primetime-Anzeigenentscheidung und eine Möglichkeit für `PlacementType.MID_ROLL` oder `PlacementType.PRE_ROLL` und `PlacementMode.FREEREPLACE`

* `CustomRangeResolver` hinzugefügt:

   * `doCanResolve()` gibt  `true` für Löschbereiche zurück.

   * `createDeleteRangeOperation()` hinzugefügt, um `DeleteRange` für die Platzierung zu erstellen

* `CustomRangeHelper` hinzugefügt:

   * Allgemeine Dienstprogrammklasse, um Mark/Delete/Replace `timeRanges` zu extrahieren und zu verarbeiten.
   * `extractCustomRangesMetadata()` hinzugefügt
   * `extractCustomRanges()` hinzugefügt
   * Hinzugefügt `mergeRanges()` - Löst Konflikte und Untergruppen/Zusammenfügungen

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()` wurde, wenn der Vorgang `DeleteRange` ist, der Aufruf zum Entfernen der Methode in dem Vorgang hinzugefügt

   * Wenn der Vorgang in `executeOperation()` `NOPTimelineOperation` (leer `AdBreaks` zurückkommt) ist, wurde der Aufruf zum Löschen hinzugefügt.

   * `onDeleteRangeComplete()` hinzugefügt
   * `removeRange()` hinzugefügt
   * Im `adjustPlacement()`-Modus für `PlacementMode.FREEREPLACE` wurde die Dauer Null gesetzt. Diese Dauer ist früher erforderlich, wenn Sie `AdBreaks` anfordern, muss sie an dieser Stelle null sein, damit sie rein eingefügt werden kann.

* `VideoEngineTimeline` Hinzugefügt  `removeC3Ad()` - Aufruf  `removeByLocalTime()` für Löschbereiche

* `AdSignalingModeGenerator`

   * `doConfigure()` - Nicht auflösen, wenn keine Gelegenheit generiert wurde
   * `createInitialOpportunity()` - Erstellen Sie keine erste Chance für  `AdSignalingMode.CUSTOM_RANGE`. Das `CustomRangeOpportunityGenerator` deckt dies bereits ab.

* `DeleteRange`

   * Erweitert `TimelineOperation`.
   * Erstellt von `CustomRangeResolver` zum Löschen und Ersetzen (der Löschteil zum Ersetzen)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - Verpacken zulassen
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` Die  `accepts()` Methode wurde geändert, um Verpackungen unterschiedlicher Platzierungstypen (Pre-Roll, Mid-Roll, Post-Roll) zu ermöglichen

* `AuditudeRequestHelper` Fehlerkorrekturen, die eine Serveraußer Kraft setzen von Anzeigenparametern ermöglichen

* `AuditudeResolver` Die  `canBePacked()` Methode wurde geändert, um Verpackungen zuzulassen

* `CustomAdResolver` Die Funktionen  `timeRange` Extraktion wurden entfernt. Wir erhalten jeweils eine Platzierung und machen daraus ein `AdBreakPlacement timelineOperation`.

