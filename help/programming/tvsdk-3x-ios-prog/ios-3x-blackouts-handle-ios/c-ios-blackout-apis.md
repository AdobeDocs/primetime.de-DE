---
description: TVSDK bietet API-Elemente, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.
title: Blackout-API-Elemente
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Blackout-API-Elemente {#blackout-api-elements}

TVSDK bietet API-Elemente, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihren Player implementieren.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die derzeit geladene Ressource als Hintergrundressource. Wenn `replaceCurrentItemWithPlayerItem` nach dieser Methode aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem` , `stop`oder `reset` .

   * `unregisterCurrentBackgroundItem` Setzt das Hintergrundelement auf nil und stoppt das Abrufen und Parsen des Hintergrundmanifests.

* **PTMetadata.PTBlackMetadata** A `PTMetadata` -Klasse, die für Blackouts spezifisch ist.

  Auf diese Weise können Sie nicht suchbare Bereiche festlegen (ein Array von `CMTimeRanges`) auf TVSDK. TVSDK sucht jedes Mal, wenn der Benutzer eine Suche durchführt, nach diesen Bereichen. Wenn sie festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer zum Ende des nicht suchbaren Bereichs.

* **HIER ALS NÄCHSTES STARTEN** **PTAdMetadata** Aktivieren oder deaktivieren Sie die Pre-roll-Funktion in einem Live-Stream durch Festlegen von `enableLivePreroll` auf JA oder NEIN. Falls NEIN, führt TVSDK vor der Wiedergabe des Inhalts keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen durch und gibt daher keine Pre-Roll-Wiedergabe ab. Dies hat keine Auswirkungen auf die Mid-Roll. Die Standardeinstellung ist JA.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Wird gepostet, wenn TVSDK ein abonniertes Tag im Hintergrundmanifest und ein neues `PTTimedMetadata` -Instanz darauf vorbereitet ist. Das Objekt der Benachrichtigung ist das `PTMediaPlayerItem` -Instanz, die derzeit wiedergegeben wird. Sie können die `PTTimedMetadata` -Instanz aus dem `userInfo` Wörterbuch mit der `PTTimedMetadataKey` Schlüssel.

   * `PTBackgroundManifestErrorNotification` - Wird gepostet, wenn der Medienplayer das Hintergrundmanifest vollständig nicht lädt, d. h. alle Stream-URLs entweder einen Fehler oder eine ungültige Antwort zurückgeben. Das Objekt der Benachrichtigung ist das `PTMediaPlayerItem` -Instanz, die derzeit wiedergegeben wird.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Herunterladen des Hintergrundmanifests.

   * `INVALID_SEEK_WARNING` Wird ausgelöst, wenn eine Suche in einem nicht suchbaren Bereich versucht wird (in `nonSeekableRanges` festgelegt in `PTBlackoutMetadata`).
