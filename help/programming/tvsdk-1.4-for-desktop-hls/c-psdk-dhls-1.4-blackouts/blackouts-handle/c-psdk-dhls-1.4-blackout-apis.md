---
description: TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
title: Blackout-API-Elemente
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Blackout-API-Elemente{#blackout-api-elements}

TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihrem Player implementieren.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die aktuell geladene Ressource als Hintergrundressource. Wenn nach dieser Methode `replaceCurrentResource` aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem` aufrufen.

   * `unregisterCurrentBackgroundItem`  Löscht die derzeit eingestellte Hintergrundressource und beendet das Abrufen und Parsen des Hintergrundmanifests.

* **** BlackoutMetadataEin Metadatentyp, der für Blackouts spezifisch ist.

   Auf diese Weise können Sie nicht suchbare Bereiche (ein zusätzliches `TimeRange`-Attribut namens `nonseekableRange`) für TVSDK festlegen. TVSDK überprüft jedes Mal, wenn der Benutzer eine Suche durchführt, auf diese Bereiche (ob die gewünschte Suchposition in einem `nonseekableRange` liegt). Wenn sie festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer bis zum Ende der `seekableRange`-Zeit.

* **Beginn HIER** **** NEXTDefaultMetadataKeysAktivieren oder deaktivieren Sie die Vorgabe für einen Live-Stream, indem Sie  `ENABLE_LIVE_PREROLL` auf true oder false einstellen. Bei &quot;false&quot;führt TVSDK keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen vor der Inhaltswiedergabe durch und gibt somit keine Pre-Roll-Wiedergabe ab. Dies hat keine Auswirkungen auf die mittleren Rollen. Die Standardeinstellung ist &quot;true&quot;.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` Ereignis-Subtyp: Wird ausgelöst, wenn TVSDK ein abonniertes Tag im Hintergrundmanifest erkennt.

* **Benachrichtigungen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Download des Hintergrundmanifests.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` Wird ausgelöst, wenn eine Suche in einem nicht suchbaren Bereich versucht wird.


