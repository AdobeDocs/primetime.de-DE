---
description: Sie können Blackouts in Live-Video-Streams handhaben und alternative Inhalte während einer Blackout-Phase bereitstellen.
title: Blackout-API-Elemente
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Blackout-API-Elemente{#blackout-api-elements}

Sie können Blackouts in Live-Video-Streams handhaben und alternative Inhalte während einer Blackout-Phase bereitstellen.

Wenn in einem Live-Stream ein Blackout auftritt, verwendet Ihr Player Ereignis-Handler, um die Blackout-Meldung zu erkennen und Benutzern, die nicht zum Anzeigen des Hauptstreams berechtigt sind, alternative Inhalte bereitzustellen. Ihr Player erkennt den Start und das Ende der Blackout-Zeit, wechselt die Wiedergabe vom Hauptstrom in einen alternativen Stream und wechselt zum Hauptstrom zurück, wenn die Blackout-Phase endet.

So handhaben Sie Stromausfälle in Live-Streams:

1. Richten Sie Ihre App so ein, dass Blackout-Tags erkannt werden, indem Sie Blackout-Tags in einem Live-Stream-Manifest abonnieren.

   TVSDK erkennt keine Blackout-Tags allein. Sie müssen Blackout-Tags abonnieren, um Benachrichtigungen zu erhalten, wenn die Tags beim Parsen der Manifestdatei gefunden werden.
1. Erstellen Sie Ereignis-Listener für Tags, für die Ihr Player angemeldet ist (in diesem Fall PLAYBACK- und BLACKOUTS-Tags) .

   Wenn ein Tag auftritt, das Ihr Player abonniert hat (z. B. ein Blackout-Tag), entweder in den Vordergrund- (Hauptinhalt) oder im Hintergrund (alternative Inhalte)-Stream-Manifesten, sendet TVSDK eine `TimedMetadataEvent` und erstellt eine `TimedMetadataObject` für die `TimedMetadataEvent`.

1. Implementieren Sie Handler für die zeitgesteuerten Metadaten-Ereignisse für die Vordergrund- und die Hintergrundstreams.

   Rufen Sie in diesen Handlern die Start- und Endzeiten für den Blackout-Zeitraum von den zeitgesteuerten Metadaten-Ereignisobjekten ab.
1. Erstellen Sie Methoden zum Wechseln von Inhalten zu Beginn und am Ende des Blackout-Zeitraums.

   Wenn der Blackout-Zeitraum beginnt, wechseln Sie den Hauptinhalt in den Hintergrund und wechseln Sie den alternativen Inhalt in den Hauptstrom. Rufen Sie das ursprüngliche Manifest im Hintergrund ab und analysieren Sie es weiter und suchen Sie nach dem Tag &quot;Blackout-Ende&quot;, damit der Player wieder in den ursprünglichen Stream eintreten kann, wenn das Blackout beendet wird.
1. Aktualisieren Sie nicht suchbare Bereiche, wenn sich der Blackout-Bereich im Wiedergabestream in DVR befindet.

   Verfolgen und Verarbeiten der `TimedMetadata` im Hintergrundstrom durch Vorbereitung und Aktualisierung nicht suchbarer Bereiche.

TVSDK bietet API-Elemente, die bei der Implementierung von Blackouts nützlich sind, einschließlich Methoden, Metadaten und Benachrichtigungen.

Sie können Folgendes verwenden, wenn Sie eine Blackout-Lösung in Ihren Player implementieren.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Speichert die derzeit geladene Ressource als Hintergrundressource. Wenn `replaceCurrentResource` nach dieser Methode aufgerufen wird, lädt TVSDK das Manifest des Hintergrundelements weiter herunter, bis Sie `unregisterCurrentBackgroundItem`, `release`oder `reset`.

   * `unregisterCurrentBackgroundItem` Setzt das Hintergrundelement auf null und stoppt das Abrufen und Parsen des Hintergrundmanifests.

* **BlackoutMetadata** -

  Eine Metadatenklasse, die speziell für Blackouts gilt.

  Auf diese Weise können Sie nicht suchbare Bereiche (ein Array von `TimeRanges`) auf TVSDK. TVSDK sucht jedes Mal, wenn der Benutzer eine Suche durchführt, nach diesen Bereichen. Wenn sie festgelegt ist und der Benutzer in einen nicht suchbaren Bereich sucht, zwingt TVSDK den Viewer zum Ende des nicht suchbaren Bereichs.

* **STARTEN SIE HIER NEXT AdvertisingMetadata .** Aktivieren oder deaktivieren Sie die Vorgabe für einen Live-Stream, indem Sie `enableLivePreroll` auf &quot;true&quot;oder &quot;false&quot;fest. Bei &quot;false&quot;führt TVSDK keinen expliziten Ad-Server-Aufruf für Pre-Roll-Anzeigen vor der Inhaltswiedergabe durch und gibt daher die Pre-Roll-Wiedergabe nicht wieder. Dies hat keine Auswirkungen auf die Mid-Roll. Der Standardwert ist &quot;true&quot;.

* **MediaPlayer.BlackoutsEventListener**

   * `onTimedMetadataInBackgroundItem` - Wird ausgelöst, wenn ein abonniertes Tag im Hintergrundmanifest und ein neues `TimedMetadata` -Instanz darauf vorbereitet ist. Die `TimedMetadata` -Instanz wird als Parameter gesendet.

   * `onBackgroundManifestFailed` : Wird ausgelöst, wenn der Medienplayer das Hintergrundmanifest vollständig nicht lädt, d. h. alle Stream-URLs entweder einen Fehler oder eine ungültige Antwort zurückgeben.

* **Benachrichtigungen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Typ: Warnung
      * Fehler beim Herunterladen des Hintergrundmanifests.
