---
description: Sie können Blackouts in Live-Videostreams bearbeiten und alternative Inhalte während einer Blackout-Phase bereitstellen.
seo-description: Sie können Blackouts in Live-Videostreams bearbeiten und alternative Inhalte während einer Blackout-Phase bereitstellen.
seo-title: Blackout-API-Elemente
title: Blackout-API-Elemente
uuid: 263a8987-0c85-493a-9352-9605c877ba65
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Blackout-API-Elemente{#blackout-api-elements}

Sie können Blackouts in Live-Videostreams bearbeiten und alternative Inhalte während einer Blackout-Phase bereitstellen.

Wenn eine Blackout-Meldung in einem Live-Stream auftritt, verwendet Ihr Player Ereignis-Handler, um die Blackout-Meldung zu erkennen und Benutzern, die nicht berechtigt sind, den Hauptstrom anzuschauen, alternative Inhalte bereitzustellen. Ihr Player erkennt den Beginn und das Ende der Blackout-Phase, wechselt die Wiedergabe vom Hauptstrom in einen alternativen Stream und wechselt zum Hauptstrom zurück, wenn die Blackout-Phase endet.

So behandeln Sie Blackouts in Live-Streams:

1. Richten Sie Ihre App so ein, dass Blackout-Tags erkannt werden, indem Sie Blackout-Tags in einem Live-Stream-Manifest abonnieren.

   TVSDK erkennt keine Blackout-Tags allein. Sie müssen Blackout-Tags abonnieren, um eine Benachrichtigung zu erhalten, wenn die Tags während der Analyse der Manifestdatei gefunden werden.
1. Erstellen Sie Ereignis-Listener für Tags, für die Ihr Player abonniert wird (in diesem Fall PLAYBACK- und BLACKOUTS-Tags).

   Wenn ein Tag auftritt, das Ihr Player abonniert hat (z. B. ein Blackout-Tag), entweder im Vordergrund (Hauptinhalt) oder im Hintergrund (alternativer Inhalt), löst TVSDK ein `TimedMetadataEvent` aus und erstellt ein `TimedMetadataObject` für das `TimedMetadataEvent`.

1. Implementieren Sie Handler für die zeitgesteuerten Metadaten-Ereignis für den Vordergrund- und den Hintergrund-Stream.

   Rufen Sie in diesen Handlern die Beginns- und Endzeiten für die Sperrfrist von den zeitgesteuerten Metadaten-Ereignis-Objekten ab.
1. Erstellen Sie Methoden zum Wechseln von Inhalten am Beginn und am Ende der Sperrfrist.

   Wenn die Sperrfrist Beginn ist, wechseln Sie den Hauptinhalt in den Hintergrund und wechseln Sie zum alternativen Inhalt, um der Hauptstrom zu werden. Rufen Sie weiterhin das ursprüngliche Manifest im Hintergrund ab und analysieren Sie es und suchen Sie nach dem Tag &quot;Blackout End&quot;, damit der Player wieder am ursprünglichen Stream teilnehmen kann, wenn das Blackout beendet wird.
1. Aktualisieren Sie nicht suchbare Bereiche, wenn sich der Blackout-Bereich im DVR-Bereich im Wiedergabestream befindet.

   Verfolgen und behandeln Sie die `TimedMetadata` im Hintergrundstream, indem Sie nicht suchbare Bereiche vorbereiten und aktualisieren.

TVSDK stellt API-Elemente bereit, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihrem Player implementieren.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die aktuell geladene Ressource als Hintergrundressource. Wenn nach dieser Methode `replaceCurrentResource` aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem`, `release` oder `reset` aufrufen.

   * `unregisterCurrentBackgroundItem` Setzt das Hintergrundelement auf null und beendet das Abrufen und Parsen des Hintergrundmanifests.

* **BlackoutMetadata** -

   Eine Metadatenklasse, die für Blackouts spezifisch ist.

   Dadurch können Sie nicht suchbare Bereiche (ein Array von `TimeRanges`) für TVSDK festlegen. TVSDK prüft jedes Mal, wenn der Benutzer eine Suche nach diesen Bereichen durchführt. Wenn es festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer bis zum Ende des nicht suchbaren Bereichs.

* **BEGINN HIER NEXT** AdvertisingMetadataAktivieren oder deaktivieren Sie die Vorgabe für einen Live-Stream, indem Sie  `enableLivePreroll` auf true oder false einstellen. Bei &quot;false&quot;führt TVSDK keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen vor der Inhaltswiedergabe durch und gibt somit keine Pre-Roll-Wiedergabe ab. Dies hat keine Auswirkungen auf die mittleren Rollen. Die Standardeinstellung ist &quot;true&quot;.

* **MediaPlayer.BlackoutsEventListener**

   * `onTimedMetadataInBackgroundItem` - Wird ausgelöst, wenn ein abonniertes Tag im Hintergrundmanifest erkannt und eine neue  `TimedMetadata` Instanz davon vorbereitet wird. Die `TimedMetadata`-Instanz wird als Parameter gesendet.

   * `onBackgroundManifestFailed` - Wird ausgelöst, wenn der Medienplayer das Hintergrundmanifest nicht vollständig lädt, d. h. alle Stream-URLs eine Fehlermeldung oder eine ungültige Antwort zurückgeben.

* **Benachrichtigungen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Download des Hintergrundmanifests.