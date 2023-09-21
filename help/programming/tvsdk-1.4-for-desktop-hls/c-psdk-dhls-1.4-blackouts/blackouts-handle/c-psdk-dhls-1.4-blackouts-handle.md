---
description: Sie können Blackouts in Live-Video-Streams handhaben und alternative Inhalte während einer Blackout-Phase bereitstellen.
title: Umgang mit Stromausfällen in Live-Streams
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Umgang mit Stromausfällen in Live-Streams{#handle-blackouts-in-live-streams}

Sie können Blackouts in Live-Video-Streams handhaben und alternative Inhalte während einer Blackout-Phase bereitstellen.

Wenn in einem Live-Stream ein Blackout auftritt, verwendet Ihr Player Ereignis-Handler, um die Blackout-Meldung zu erkennen und Benutzern, die nicht zum Anzeigen des Hauptstreams berechtigt sind, alternative Inhalte bereitzustellen. Ihr Player erkennt den Start und das Ende der Blackout-Zeit, wechselt die Wiedergabe vom Hauptstrom in einen alternativen Stream und wechselt zum Hauptstrom zurück, wenn die Blackout-Phase endet.

In Ihrer Client-App abonnieren Sie Blackout-Tags in TVSDK. Nach der Benachrichtigung über neue *zeitgesteuerte Metadaten* -Objekte analysieren Sie die Daten des zeitgesteuerten Metadatenobjekts, um festzustellen, ob das Objekt einen Blackout-Einstieg oder -Ausstieg anzeigt. Bei identifizierten Blackouts rufen Sie die relevanten TVSDK-Elemente auf, um zu Beginn des Blackouts zu alternativen Inhalten zu wechseln und wieder zum Hauptinhalt zurückzukehren, wenn der Blackout beendet ist.

>[!TIP]
>
>Die Schlüssel werden weiterhin aus dem Manifest heruntergeladen, bevor der Inhalt wiedergegeben wird.

Wenn ein Benutzer eine Verbindung zu einem Live-Stream herstellt, nachdem die Blackout-Phase beendet ist, und wieder in die Phase des Ausblendens scrollt, wird der Inhalt wiedergegeben.

>[!IMPORTANT]
>
>Wenn alle Schlüsselanforderungen fehlschlagen, wird beim Analysieren des Manifests ein Fehler ausgegeben. Wenn einige Anforderungen fehlschlagen und einige erfolgreich sind, versucht TVSDK, den Inhalt wiederzugeben. Wenn TVSDK versucht, einen Abschnitt des Inhalts wiederzugeben, aber kein gültiger Schlüssel zum Entschlüsseln dieses Inhalts vorhanden ist, wird ein Fehler zurückgegeben.

So handhaben Sie Stromausfälle in Live-Streams:

1. Richten Sie Ihre App so ein, dass Blackout-Tags erkannt werden, indem Sie Blackout-Tags in einem Live-Stream-Manifest abonnieren.

   TVSDK erkennt keine Blackout-Tags allein. Sie müssen Blackout-Tags abonnieren, um Benachrichtigungen zu erhalten, wenn die Tags beim Parsen der Manifestdatei gefunden werden.
1. Erstellen Sie Ereignis-Listener für Tags, für die Ihr Player angemeldet ist.

   Wenn ein Tag auftritt, das Ihr Player abonniert hat (z. B. ein Blackout-Tag), entweder in den Vordergrund- (Hauptinhalt) oder im Hintergrund (alternative Inhalte)-Stream-Manifesten, sendet TVSDK eine `TimedMetadataEvent` und erstellt eine `TimedMetadataObject` für die `TimedMetadataEvent`.
1. Implementieren Sie Handler für die zeitgesteuerten Metadaten-Ereignisse für die Vordergrund- und die Hintergrundstreams.

   Rufen Sie in diesen Handlern die Start- und Endzeiten für den Blackout-Zeitraum von den zeitgesteuerten Metadaten-Ereignisobjekten ab.
1. Bereiten Sie die `MediaPlayer` für Stromausfälle.

   Wenn die Variable `MediaPlayer` Wechselt in den Status VORBEREITT , berechnen und bereiten Sie die Blackout-Bereiche vor und legen Sie sie auf der `MediaPlayer` Objekt.

1. Überprüfen Sie für jede Aktualisierung der Abspielposition die Liste der `TimedMetadataObjects`.

   Hier erkennt Ihr Player den Start und das Ende der Blackout-Aktion und zeichnet die Zeit der Blackout-Aktion auf, sobald sie eintritt.

1. Erstellen Sie Methoden zum Wechseln von Inhalten zu Beginn und am Ende des Blackout-Zeitraums.

   Wenn der Blackout-Zeitraum beginnt, wechseln Sie den Hauptinhalt in den Hintergrund und wechseln Sie den alternativen Inhalt in den Hauptstrom. Rufen Sie das ursprüngliche Manifest im Hintergrund ab und analysieren Sie es weiter und suchen Sie nach dem Tag &quot;Blackout-Ende&quot;, damit der Player wieder in den ursprünglichen Stream eintreten kann, wenn das Blackout beendet wird.
