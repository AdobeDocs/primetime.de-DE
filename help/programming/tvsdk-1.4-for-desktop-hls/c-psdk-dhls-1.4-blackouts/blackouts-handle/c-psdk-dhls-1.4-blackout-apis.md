---
description: TVSDK bietet API-Elemente, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
title: Blackout-API-Elemente
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Blackout-API-Elemente{#blackout-api-elements}

TVSDK bietet API-Elemente, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihren Player implementieren.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die derzeit geladene Ressource als Hintergrundressource. Wenn `replaceCurrentResource` nach dieser Methode aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  Löscht die derzeit eingestellte Hintergrundressource und stoppt das Abrufen und Parsen des Hintergrundmanifests.

* **BlackoutMetadata** Ein Metadatentyp, der für Blackouts spezifisch ist.

  Auf diese Weise können Sie nicht suchbare Bereiche festlegen (eine zusätzliche `TimeRange` Attribut genannt `nonseekableRange`) auf TVSDK. TVSDK prüft diese Bereiche (ob die gewünschte Suchposition in einer `nonseekableRange`) jedes Mal, wenn der Benutzer eine Suche durchführt. Wenn sie festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer zum Endzeitpunkt des `seekableRange`.

* **HIER ALS NÄCHSTES STARTEN** **DefaultMetadataKeys** Aktivieren oder deaktivieren Sie die Vorgabe für einen Live-Stream, indem Sie `ENABLE_LIVE_PREROLL` auf &quot;true&quot;oder &quot;false&quot;fest. Bei &quot;false&quot;führt TVSDK keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen vor der Inhaltswiedergabe durch und gibt daher die Pre-Roll-Wiedergabe nicht wieder. Dies hat keine Auswirkungen auf die Mid-Roll. Der Standardwert ist &quot;true&quot;.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` event subtype - Wird ausgelöst, wenn TVSDK ein abonniertes Tag im Hintergrundmanifest erkennt.

* **Benachrichtigungen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Herunterladen des Hintergrundmanifests.

   * `SeekEvent.SEEK_POSITION_ADJUSTED` Wird ausgelöst, wenn eine Suche in einem nicht suchbaren Bereich versucht wird.
