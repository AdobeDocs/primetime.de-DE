---
description: Diese Änderungen an der Android TVSDK-API unterstützen das Löschen und Ersetzen von Anzeigen.
title: API-Änderungen beim Löschen und Ersetzen von Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# API-Änderungen beim Löschen und Ersetzen von Anzeigen{#ad-deletion-and-replacement-api-changes}

Diese Änderungen an der Android TVSDK-API unterstützen das Löschen und Ersetzen von Anzeigen.

* `AdSignalingMode` Neuer benutzerdefinierter Anzeigeanzeigemodus für den Zeitraum

* `AdvertisingMetadata` Neu `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Legt die Zeiträume fest, die bei der Verarbeitung von Metadaten markiert, gelöscht oder ersetzt werden sollen

* `ContentResolver`

   * Neu `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Neu `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Neu `ContentRemoval` class

  `TimelineOperation` -Klasse, die den Zeitraum definiert, der aus der Timeline entfernt werden soll

* `AuditudeResolver`

   * Neu `private LinkedList<AuditudeRequest> _requestQueue`
   * Neu `void startConsumer()`: Startet die Verarbeitung der Anforderungswarteschlange für die Primetime-Anzeigenentscheidung und stellt sicher, dass jede Anforderung in `MIN_INIT_REQUEST_INTERVAL` Intervalle

   * Neu `processReplacementRange()`: Extrahiert Zeiträume aus den Anzeigenmetadaten und generiert `PlacementInformations`und erstellt eine Primetime-Anzeigenentscheidungsanforderung mit dem `PlacementInformations`.

   * Neu `canDoResolver()`: Überprüft, ob die Platzierungsmöglichkeit Primetime-Anzeigenentscheidungen-Metadaten enthält

* Neu `CustomRangeHelper` Hilfsklasse, die Zeitbereichsmetadaten aus Anzeigenmetadaten extrahiert und Teilmengen/Überschneidungen/ungültige Zeiträume entfernt.

* Neu `DeleteContentResolver` Content Resolver, der die Platzierungsmöglichkeiten von `PlacementInformation.Mode.DELETE`

* Neu `NopTimelineOperation` Neuer Timeline-Vorgang für den Fall, dass keine Platzierung oder Ersetzung von Werbeunterbrechungen erforderlich ist. Diese Klasse wird verwendet, um zwischen diesem und dem Auftreten eines Fehlers während des Auflösungsprozesses zu unterscheiden.

* `TimelineOperationQueue` Prüft, ob der Timeline-Vorgang ein `NopTimelineOperation` vor der Verarbeitung.

* `CustomAdMarkersContentResolver` Neu `canDoResolve()`: Prüft, ob eine Platzierungsmöglichkeit vom Typ `Mode.MARK`

* `MetadataResolver` Neu `canDoResolve()`: Prüft, ob eine Platzierungsmöglichkeit vom Typ `Mode.INSERT`

* `DefaultMetadataKeys` Neu `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Neuer Modus `enum (INSERT, DELETE, REPLACE, MARK)`
   * Neuer Typ `CUSTOM_TIME_RANGES`

* `TimeRange` Neu `compareTo(TimeRange timeRange)`: So können Sie TimeRanges basierend auf der Startzeit sortieren.

* Neu `ReplacementTimeRange` Erweitert die `TimeRange` -Klasse, die den Ersatzwert darstellt, mit einer `begin`, `end`, und `replacement-duration` -Parameter.

* `TimeRangeCollection`

   * Neu `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Umbenannt `CUSTOM_AD_MARKERS` nach `MARK_RANGES`

   * Geändert `toMetadata(Metadata options)` zum Löschen/Markieren/Ersetzen von Bereichen in Anzeigenmetadaten.

* `MediaPlayerNotification`

   * Neu `UNDEFINED_TIME_RANGES`: Wenn der Anzeigesignalmodus Server Map oder Manifest Cues lautet und die Ersetzungsbereiche auch in den Anzeigenmetadaten enthalten sind, werden die Ersetzungsbereiche ignoriert.
   * Neu `REPLACE_RANGES_NOT_AVAILABLE`: Wenn der Anzeigesignalmodus Benutzerdefinierte Zeitbereiche ist und keine Ersatzbereiche verfügbar sind, wird eine Warnung gesendet.

* `AdvertisingFactory` Neu `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Neu `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Neu `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`: Sucht beim ersten Versuch nach 0, da der Wert bei einem Bereich liegt. `[0,n]` gelöscht wird, wird der Medienplayer nicht automatisch wiedergegeben.

   * In `prepareToPlay()`: Durchläuft die Liste der Informationen zur ersten Platzierung für `mediaplayerclient` auflösen.

   * In `extractAdSignalingMode()`: Für den neuen benutzerdefinierten Zeitbereichsmodus geeignet.
   * Neu `private static List<PlacementInformation> createInitalPlacementInformations()`: Erstellt die anfänglichen Platzierungsinformationen für den Anzeigensignalisierungsmodus und die Inhaltsauflöser (abgeleitet aus Anzeigenmetadaten).
   * In `ContentPlacementCompletedListener`: Prüft, ob `mediaPlayerClient` is `doneInitialResolving` vor Aufruf `endAdResolving`.

* `MediaPlayerClient`

   * Neu `List<ContentResolver> _contentResolvers`
   * Neu `int _reservations`
   * Neu `lookupContentResolver(PlacementOpportunity placementOpportunity)`: Sucht, welcher Resolver die `PlacementOpportunity`.

   * Der Code wurde geändert, um mehrere Inhaltsauflöser zu erstellen.
   * Neu `public boolean doneInitialResolving()`: Prüft, ob noch Möglichkeiten bestehen, die gelöst werden müssen.

* `VideoEngineTimeline`

   * Neu `removeContent(TimelineOperation timelineOperation)`: Entfernt einen bestimmten Inhaltsbereich aus der Timeline.
   * Neu `removeContentByLocalTime(long begin, long end)`: Entfernt den Inhalt nach der angegebenen lokalen Zeit `begin` und `end`.

* `DefaultOpportunityDetectorFactory` Geändert `createOpportunityDetector`: Geben Sie für VOD-Streams nur einen neuen `SpliceOutOpportunityDetector` wenn keine MÄRK- oder ERSETZUNGSbereiche vorhanden sind (da diese Bereiche Vorrang vor dem Signalmodus haben).
