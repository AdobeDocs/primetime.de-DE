---
description: Diese Änderungen an der Android TVSDK API unterstützen das Löschen und Ersetzen von Anzeigen.
seo-description: Diese Änderungen an der Android TVSDK API unterstützen das Löschen und Ersetzen von Anzeigen.
seo-title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
title: Änderungen an der API zum Löschen und Ersetzen von Anzeigen
uuid: 2bb8a331-6851-4442-99de-b01500a0e1e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Änderungen an der Anzeigen-Löschungs- und Ersatz-API{#ad-deletion-and-replacement-api-changes}

Diese Änderungen an der Android TVSDK API unterstützen das Löschen und Ersetzen von Anzeigen.

* `AdSignalingMode` Neuer benutzerdefinierter Zeitbereich-Anzeigensignaturmodus

* `AdvertisingMetadata` Neu  `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Legt die Zeitbereiche fest, die beim Verarbeiten von Metadaten markiert, gelöscht oder ersetzt werden sollen

* `ContentResolver`

   * Neu `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Neu `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Neue `ContentRemoval`-Klasse

   `TimelineOperation` -Klasse, die den Zeitraum definiert, der aus der Zeitleiste entfernt werden soll

* `AuditudeResolver`

   * Neu `private LinkedList<AuditudeRequest> _requestQueue`
   * Neu `void startConsumer()`: Beginn, die die Anforderungswarteschlange für die Primetime-Anzeigenentscheidung bearbeiten, stellen sicher, dass jede Anforderung in `MIN_INIT_REQUEST_INTERVAL`-Intervallen ausgegeben wird

   * Neu `processReplacementRange()`: Extrahiert Zeiträume aus den Anzeigenmetadaten und generiert `PlacementInformations` und erstellt eine Primetime-Anfrage zur Anzeigenentscheidung, die das `PlacementInformations` enthält.

   * Neu `canDoResolver()`: Überprüft, ob die Platzierungsmöglichkeit über Primetime-Anzeigenentscheidungsmetadaten verfügt

* Neue `CustomRangeHelper` Helper-Klasse, die Zeitraummetadaten aus Anzeigenmetadaten extrahiert und Untergruppen/Überschneidungen/ungültige Zeiträume entfernt.

* Neuer Inhaltsauflöser `DeleteContentResolver`, der die Platzierungsmöglichkeiten von `PlacementInformation.Mode.DELETE` auflöst

* Neuer `NopTimelineOperation` Neuer Timeline-Vorgang für den Fall, dass keine Platzierung von Werbeunterbrechungen oder kein Austausch erfolgen muss. Mit dieser Klasse wird unterschieden, ob dies der Fall ist und wann während des Auflösungsvorgangs ein Fehler auftritt.

* `TimelineOperationQueue` Überprüft, ob der Zeitschienenvorgang  `NopTimelineOperation` vor der Verarbeitung durchgeführt wird.

* `CustomAdMarkersContentResolver` Neu  `canDoResolve()`: Prüft, ob eine Platzierungsmöglichkeit vom Typ  `Mode.MARK`

* `MetadataResolver` Neu  `canDoResolve()`: Prüft, ob eine Platzierungsmöglichkeit vom Typ  `Mode.INSERT`

* `DefaultMetadataKeys` Neu  `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Neuer Modus `enum (INSERT, DELETE, REPLACE, MARK)`
   * Neuer Typ `CUSTOM_TIME_RANGES`

* `TimeRange` Neu  `compareTo(TimeRange timeRange)`: So können Sie TimeRanges basierend auf der Startzeit sortieren

* Neu `ReplacementTimeRange` Erweitert die `TimeRange`-Klasse, die eine Ersatzzeit darstellt, mit einem `begin`-, `end`- und `replacement-duration`-Parameter.

* `TimeRangeCollection`

   * Neu `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Umbenannt in `CUSTOM_AD_MARKERS` in `MARK_RANGES`

   * `toMetadata(Metadata options)` wurde geändert, um Bereiche zum Löschen/Markieren/Ersetzen in Anzeigenmetadaten einzufügen.

* `MediaPlayerNotification`

   * Neu `UNDEFINED_TIME_RANGES`: Wenn der Anzeigensignalisierungsmodus &quot;Serverzuordnung&quot;oder &quot;Manifestfarben&quot;lautet und die Ersetzungsbereiche auch in den Anzeigenmetadaten enthalten sind, werden die Ersetzungsbereiche ignoriert.
   * Neu `REPLACE_RANGES_NOT_AVAILABLE`: Wenn der Anzeigensignalisierungsmodus &quot;Benutzerdefinierte Zeitbereiche&quot;ist und keine Ersatzbereiche verfügbar sind, wird eine Warnung ausgelöst.

* `AdvertisingFactory` Neu  `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Neu  `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Neu  `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`: Sucht zunächst nach 0, da der Medienplayer nicht automatisch abgespielt wird, wenn der Bereich `[0,n]` gelöscht wird.

   * In `prepareToPlay()`: Schleifen durch die Liste der anfänglichen Platzierungsinformationen für die Auflösung von `mediaplayerclient`.

   * In `extractAdSignalingMode()`: Für den neuen benutzerdefinierten Zeitraum-Modus anpassen.
   * Neu `private static List<PlacementInformation> createInitalPlacementInformations()`: Generiert die anfänglichen Platzierungsinformationen für den Anzeigensignalisierungsmodus und Inhaltsauflöser (abgeleitet von Anzeigenmetadaten).
   * In `ContentPlacementCompletedListener`: Prüft, ob `mediaPlayerClient` `doneInitialResolving` vor dem Aufruf von `endAdResolving` ist.

* `MediaPlayerClient`

   * Neu `List<ContentResolver> _contentResolvers`
   * Neu `int _reservations`
   * Neu `lookupContentResolver(PlacementOpportunity placementOpportunity)`: Sucht, welcher Auflöser das `PlacementOpportunity` auflösen kann.

   * Modifizierter Code zum Erstellen mehrerer Content-Auflöser.
   * Neu `public boolean doneInitialResolving()`: Überprüft, ob noch Möglichkeiten zur Lösung vorhanden sind.

* `VideoEngineTimeline`

   * Neu `removeContent(TimelineOperation timelineOperation)`: Entfernt einen bestimmten Inhaltsbereich aus der Zeitleiste.
   * Neu `removeContentByLocalTime(long begin, long end)`: Entfernt Inhalt nach lokaler Zeit, angegeben `begin` und `end`.

* `DefaultOpportunityDetectorFactory` Geändert  `createOpportunityDetector`: Bei VOD-Streams wird nur ein neuer Wert zurückgegeben,  `SpliceOutOpportunityDetector` wenn es keine MARK- oder REPLACE-Bereiche gibt (da diese Bereiche Vorrang vor dem Signalmodus haben).

