---
description: TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
seo-description: TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
seo-title: Blackout-API-Elemente
title: Blackout-API-Elemente
uuid: ddc81558-4218-44d2-92df-15926c7c96b3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Blackout-API-Elemente{#blackout-api-elements}

TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihrem Player implementieren.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die aktuell geladene Ressource als Hintergrundressource. Wenn nach dieser Methode aufgerufen `replaceCurrentItemWithPlayerItem` wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem` , `stop`oder `reset` aufrufen.

   * `unregisterCurrentBackgroundItem` Setzt das Hintergrundelement auf null und beendet das Abrufen und Parsen des Hintergrundmanifests.

* **PTMetadata.PTBlackoutMetadata** Eine `PTMetadata` Klasse, die für Blackouts spezifisch ist.

   Dadurch können Sie nicht suchbare Bereiche (ein Array von `CMTimeRanges`) für TVSDK festlegen. TVSDK prüft jedes Mal, wenn der Benutzer eine Suche nach diesen Bereichen durchführt. Wenn es festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer bis zum Ende des nicht suchbaren Bereichs.

* **BEGINN HIER NEXT** **PTAdMetadata** Aktivieren oder deaktivieren Sie die Pre-Roll-Funktion für einen Live-Stream durch Einstellung `enableLivePreroll` auf YES oder NO. Wenn NO, gibt TVSDK vor der Inhaltswiedergabe keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen aus und spielt daher nicht die Pre-Roll-Wiedergabe ab. Dies hat keine Auswirkungen auf die mittleren Rollen. Die Standardeinstellung ist JA.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Wird veröffentlicht, wenn TVSDK ein abonniertes Tag im Hintergrundmanifest erkennt und eine neue `PTTimedMetadata` Instanz davon vorbereitet wird. Das Objekt der Benachrichtigung ist die `PTMediaPlayerItem` Instanz, die gerade abgespielt wird. Sie können die `PTTimedMetadata` Instanz mithilfe des `userInfo` Schlüssels aus dem `PTTimedMetadataKey` Wörterbuch der Benachrichtigung abrufen.

   * `PTBackgroundManifestErrorNotification` - Wird gepostet, wenn der Medienplayer das Hintergrundmanifest nicht vollständig lädt, d. h. alle Stream-URLs eine Fehlermeldung oder eine ungültige Antwort zurückgeben. Das Objekt der Benachrichtigung ist die `PTMediaPlayerItem` Instanz, die gerade abgespielt wird.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Download des Hintergrundmanifests.
   * `INVALID_SEEK_WARNING` Wird ausgelöst, wenn eine Suche in einem nicht suchbaren Bereich versucht wird (in `nonSeekableRanges` Abschnitt `PTBlackoutMetadata`).


