---
description: TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
title: Blackout-API-Elemente
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Blackout-API-Elemente{#blackout-api-elements}

TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihrem Player implementieren.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die aktuell geladene Ressource als Hintergrundressource. Wenn `replaceCurrentItemWithPlayerItem` nach dieser Methode aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem`, `stop` oder `reset` aufrufen.

   * `unregisterCurrentBackgroundItem` Setzt das Hintergrundelement auf null und beendet das Abrufen und Parsen des Hintergrundmanifests.

* **PTMetadata.** PTBlackoutMetadataEine für Blackouts spezifische  `PTMetadata` Klasse.

   Dadurch können Sie nicht suchbare Bereiche (ein Array von `CMTimeRanges`) für TVSDK festlegen. TVSDK prüft jedes Mal, wenn der Benutzer eine Suche nach diesen Bereichen durchführt. Wenn es festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer bis zum Ende des nicht suchbaren Bereichs.

* **Beginn HIER** **** NEXTPTAdMetadataAktivieren oder deaktivieren Sie die Vorspulen-Funktion für einen Live-Stream, indem Sie  `enableLivePreroll` auf YES oder NO festlegen. Wenn NO, gibt TVSDK vor der Inhaltswiedergabe keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen aus und spielt daher nicht die Pre-Roll-Wiedergabe ab. Dies hat keine Auswirkungen auf die mittleren Rollen. Die Standardeinstellung ist JA.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Wird veröffentlicht, wenn TVSDK ein abonniertes Tag im Hintergrundmanifest erkennt und eine neue  `PTTimedMetadata` Instanz davon vorbereitet wird. Das Objekt der Benachrichtigung ist die `PTMediaPlayerItem`-Instanz, die derzeit abgespielt wird. Sie können die `PTTimedMetadata`-Instanz aus dem `userInfo`-Wörterbuch der Benachrichtigung mit dem `PTTimedMetadataKey`-Schlüssel abrufen.

   * `PTBackgroundManifestErrorNotification` - Wird gepostet, wenn der Medienplayer das Hintergrundmanifest nicht vollständig lädt, d. h. alle Stream-URLs eine Fehlermeldung oder eine ungültige Antwort zurückgeben. Das Objekt der Benachrichtigung ist die `PTMediaPlayerItem`-Instanz, die derzeit abgespielt wird.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Download des Hintergrundmanifests.
   * `INVALID_SEEK_WARNING` Wird ausgelöst, wenn eine Suche in einem nicht suchbaren Bereich versucht wird (in  `nonSeekableRanges` Abschnitt  `PTBlackoutMetadata`).


