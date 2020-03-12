---
description: Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
seo-description: Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.
seo-title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Änderungen an der API zum Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-api-changes}

Diese Änderungen in TVSDK unterstützen das Löschen und Ersetzen von Anzeigen.

* `AdSignalingMode` Der `CUSTOM_RANGES` Signalmodus wurde hinzugefügt.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Wird eingestellt, `AdSignalingMode.CUSTOM_RANGES` wenn die Ersatzbereiche in den Metadaten enthalten sind.

* `PlacementType` Hinzugefügter `CUSTOM_RANGE` Typ.

* `PlacementMode`

   * Der `DELETE` Modus wurde hinzugefügt.
   * Hinzugefügter `MARK` Modus
   * Hinzugefügter `FreeReplace` Modus - Dieser Modus hat eine Dauer, ist jedoch eine reine Einfügung

* `TimeRange` Keine `final` Klasse mehr

* Hinzugefügte `ReplaceTimeRange()` Methode

   Erweitert `TimeRange` um eine `replacementDuration` Eigenschaft. Bei den Fällen MARK und DELETE ist `replacementDuration` der Wert 0.

* `TimeRangeCollection`

   * Die `toReplaceMetadata()` Dienstprogrammfunktion zum Extrahieren wurde hinzugefügt `timeRanges`.

   * Geändert für die Verwendung `DELETE` und `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Hinzugefügt `createCustomTimeRangesFrom()` - Erstellt Metadaten für die Anwendungsfälle MARK/DELETE/ERSETZEN aus der JSON-Datei.
   * Entfernt `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Hinzugefügt `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Hinzugefügt `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (nicht geändert)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Hinzugefügt `CustomRangesOpportunityGenerator` für den Fall, dass die Metadaten benutzerdefinierte Bereiche enthalten
   * `doRetrieveResolvers()`

      * Hinzufügen `CustomRangeResolver` für den Zeitpunkt, zu dem in den Metadaten benutzerdefinierte Bereiche &quot;LÖSCHEN&quot;und &quot;ERSETZEN&quot;vorhanden sind
      * Vor `CustomAdMarkerResolver` dem `AuditudeResolver`


* Hinzugefügt `CustomRangeOpportunityGenerator`

   * `doUpdate()` Leer lassen - kein Update, VOD
   * `doProcess()` Erstellt eine neue Platzierung eines neuen Typs `Placement.Delete_Range`

   * Am Anfang `CustomRangeOppotunityGenerator` der Generatoren-Liste in hinzugefügt, `DefaultContentFactory`sodass Löschbereiche vor Anzeigeneinfügungen verarbeitet werden.

   * Hinzugefügt, `createCustomRangeOpportunities` um alle Möglichkeiten zu schaffen

      MARK - Eine Gelegenheit für jeden gültigen Markenbereich `PlacementType.CUSTOM_RANGE` und `PlacementMode.MARK`

      LÖSCHEN - Eine Gelegenheit für jeden gültigen Löschbereich `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`

      ERSETZEN - Zwei Möglichkeiten für jeden gültigen Ersatzbereich:

      1. Eine Löschbereichsmöglichkeit von `PlacementType.CUSTOM_RANGE` und `PlacementMode.DELETE`.

      1. Eine Primetime-Anzeigenentscheidung und eine Gelegenheit für `PlacementType.MID_ROLL` oder `PlacementType.PRE_ROLL` und `PlacementMode.FREEREPLACE`

* Hinzugefügt `CustomRangeResolver`:

   * `doCanResolve()` wird `true` für Löschbereiche zurückgegeben.

   * Hinzufügen `createDeleteRangeOperation()` zur Erstellung `DeleteRange` für die Platzierung

* Hinzugefügt `CustomRangeHelper`:

   * Allgemeine Dienstprogrammklasse zum Extrahieren von Mark/Delete/Replace `timeRanges` und zum Verarbeiten.
   * Hinzugefügt `extractCustomRangesMetadata()`
   * Hinzugefügt `extractCustomRanges()`
   * Hinzugefügt `mergeRanges()` - Löst Konflikte und Untergruppen/Zusammenführungen

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()`dem, wenn der Vorgang `DeleteRange`ist, wurde der Aufruf zum Entfernen der Methode in dem Vorgang hinzugefügt

   * Wenn `executeOperation()`der Vorgang `NOPTimelineOperation` `AdBreaks` (leer, der vom Server zurückgegeben wird) ausgeführt wird, wurde der Aufruf zum Löschen hinzugefügt.

   * Hinzugefügt `onDeleteRangeComplete()`
   * Hinzugefügt `removeRange()`
   * Im `adjustPlacement()`Modus &quot; `PlacementMode.FREEREPLACE` Modus&quot;wurde die Dauer ausgeschlossen. Diese Dauer ist bei der Anforderung früher erforderlich `AdBreaks`, an diesem Punkt muss sie null sein, um reine Einfügung zu sein.

* `VideoEngineTimeline` Hinzugefügt `removeC3Ad()` - Aufruf `removeByLocalTime()` für Löschbereiche

* `AdSignalingModeGenerator`

   * `doConfigure()` - Nicht auflösen, wenn keine Gelegenheit generiert wurde
   * `createInitialOpportunity()` - Erstellen Sie keine erste Chance für `AdSignalingMode.CUSTOM_RANGE`. Das `CustomRangeOpportunityGenerator` deckt sich bereits.

* `DeleteRange`

   * Erweitert `TimelineOperation`.
   * Erstellt von `CustomRangeResolver` zum Löschen und Ersetzen (der Löschteil zum Ersetzen)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - Verpacken zulassen
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` Die `accepts()` Methode wurde geändert, um Verpackungen unterschiedlicher Platzierungstypen (Pre-Roll, Mid-Roll, Post-Roll) zu ermöglichen

* `AuditudeRequestHelper` Fehlerkorrekturen, die eine Serveraußer Kraft setzen von Anzeigenparametern ermöglichen

* `AuditudeResolver` Die `canBePacked()` Methode wurde geändert, um die Verpackung zuzulassen

* `CustomAdResolver` Die Funktionen `timeRange` Extraktion wurden entfernt. Wir bekommen jeweils eine Platzierung und machen das zu einer `AdBreakPlacement timelineOperation`.

