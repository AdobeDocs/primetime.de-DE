---
description: Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
title: API-Änderungen beim Löschen und Ersetzen von Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# API-Änderungen beim Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-api-changes}

Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.

* `AdSignalingMode` hinzugefügt `CUSTOM_RANGES` Signalmodus.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Set `AdSignalingMode.CUSTOM_RANGES` , wenn Ersetzungsbereiche in den Metadaten enthalten sind.

* `PlacementType` hinzugefügt `CUSTOM_RANGE` Typ.

* `PlacementMode`

   * hinzugefügt `DELETE` -Modus.
   * hinzugefügt `MARK` mode
   * hinzugefügt `FreeReplace` mode - Dieser Modus hat eine Dauer, ist aber eine reine Einfügung

* `TimeRange` Nicht mehr als `final` class

* hinzugefügt `ReplaceTimeRange()` method

  Erweiterungen `TimeRange` , um `replacementDuration` -Eigenschaft. Für die Fälle MARK und DELETE: `replacementDuration` ist 0.

* `TimeRangeCollection`

   * hinzugefügt `toReplaceMetadata()` Dienstprogrammfunktion zum Extrahieren `timeRanges`.

   * Geändert für die Verwendung mit `DELETE` und `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * hinzugefügt `createCustomTimeRangesFrom()` - Erstellt Metadaten für MARK/DELETE/ERSETZEN -Anwendungsfälle aus der JSON-Datei.
   * Entfernt `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * hinzugefügt `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * hinzugefügt `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (hat sich nicht geändert)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * hinzugefügt `CustomRangesOpportunityGenerator` für den Fall, dass die Metadaten benutzerdefinierte Bereiche enthalten

   * `doRetrieveResolvers()`

      * Hinzufügen `CustomRangeResolver` für den Fall, dass benutzerdefinierte Bereiche vom Typ DELETE und ERSETZEN in den Metadaten vorhanden sind
      * Verschieben `CustomAdMarkerResolver` ahead von `AuditudeResolver`

* hinzugefügt `CustomRangeOpportunityGenerator`

   * `doUpdate()` Leer lassen - kein Update, VOD
   * `doProcess()` Erstellt eine neue Platzierung eines neuen Typs `Placement.Delete_Range`

   * hinzugefügt `CustomRangeOppotunityGenerator` oben in der Liste der Stromerzeuger in `DefaultContentFactory`, sodass Löschbereiche vor Anzeigeneinfügungen verarbeitet werden.

   * hinzugefügt `createCustomRangeOpportunities` alle Möglichkeiten zu schaffen

     MARK - Eine Chance für jeden gültigen Markenbereich `PlacementType.CUSTOM_RANGE` und `PlacementMode.MARK`

     DELETE - Eine Chance für jeden gültigen Löschbereich `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`

     ERSETZEN - Zwei Möglichkeiten für jeden gültigen Ersatzbereich:

      1. Eine Löschreichweite von `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`.

      1. Eine Primetime-Anzeigenentscheidung und die Möglichkeit, `PlacementType.MID_ROLL` oder `PlacementType.PRE_ROLL` und `PlacementMode.FREEREPLACE`

* hinzugefügt `CustomRangeResolver`:

   * `doCanResolve()` return `true` für Löschbereiche.

   * hinzugefügt `createDeleteRangeOperation()` erstellen `DeleteRange` für die Platzierung

* hinzugefügt `CustomRangeHelper`:

   * Allgemeine Dienstprogrammklasse zum Extrahieren von Markierung/Löschen/Ersetzen `timeRanges` und verarbeiten sie.
   * hinzugefügt `extractCustomRangesMetadata()`
   * hinzugefügt `extractCustomRanges()`
   * hinzugefügt `mergeRanges()` - Behebt Konflikte und Teilmengen/Zusammenführungen

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()`, wenn der Vorgang `DeleteRange`hinzugefügt, Aufruf zum Entfernen der Methode im -Vorgang

   * In `executeOperation()`, wenn der Vorgang `NOPTimelineOperation` (leer `AdBreaks` zurück vom Server), wurde ein Aufruf zum Löschen hinzugefügt.

   * hinzugefügt `onDeleteRangeComplete()`
   * hinzugefügt `removeRange()`
   * In `adjustPlacement()`, für `PlacementMode.FREEREPLACE` -Modus die Dauer verkleinert. Diese Dauer ist bei Anforderung früher erforderlich `AdBreaks`, muss es an dieser Stelle Null sein, um reine Einfügung zu sein.

* `VideoEngineTimeline` hinzugefügt `removeC3Ad()` - Aufruf `removeByLocalTime()` für Löschbereiche

* `AdSignalingModeGenerator`

   * `doConfigure()` - Nicht beheben, wenn keine Gelegenheit generiert wird
   * `createInitialOpportunity()` - Generieren Sie keine erste Chance für `AdSignalingMode.CUSTOM_RANGE`. Die `CustomRangeOpportunityGenerator` deckt dies bereits ab.

* `DeleteRange`

   * Erweiterungen `TimelineOperation`.
   * Erstellt von `CustomRangeResolver` für Löschen und Ersetzen (Löschteil der Ersetzung)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - Verpackung zulassen
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` Die `accepts()` -Methode geändert, um die Verpackung verschiedener Platzierungstypen zu ermöglichen (Pre-roll, Mid-roll, Post-roll)

* `AuditudeRequestHelper` Fehlerkorrekturen, um das Serverüberschreiben von Anzeigenparametern zu ermöglichen

* `AuditudeResolver` Die `canBePacked()` -Methode geändert, um das Verpacken zu ermöglichen

* `CustomAdResolver` Die `timeRange` Extraktionsfunktionen wurden entfernt. Wir bekommen eine Platzierung nach der anderen und verwandeln sie in eine `AdBreakPlacement timelineOperation`.
