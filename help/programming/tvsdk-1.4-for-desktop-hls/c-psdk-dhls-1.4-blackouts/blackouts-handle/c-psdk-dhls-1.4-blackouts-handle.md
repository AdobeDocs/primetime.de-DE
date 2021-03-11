---
description: Sie können Blackouts in Live-Videostreams bearbeiten und alternative Inhalte während einer Blackout-Phase bereitstellen.
title: Umgang mit Stromausfällen in Live-Streams
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Umgang mit Blackouts in Live-Streams{#handle-blackouts-in-live-streams}

Sie können Blackouts in Live-Videostreams bearbeiten und alternative Inhalte während einer Blackout-Phase bereitstellen.

Wenn eine Blackout-Meldung in einem Live-Stream auftritt, verwendet Ihr Player Ereignis-Handler, um die Blackout-Meldung zu erkennen und Benutzern, die nicht berechtigt sind, den Hauptstrom anzuschauen, alternative Inhalte bereitzustellen. Ihr Player erkennt den Beginn und das Ende der Blackout-Phase, wechselt die Wiedergabe vom Hauptstrom in einen alternativen Stream und wechselt zum Hauptstrom zurück, wenn die Blackout-Phase endet.

In Ihrer Client-App abonnieren Sie Blackout-Tags in TVSDK. Nachdem Sie über neue *zeitgesteuerte Metadaten*-Objekte benachrichtigt wurden, analysieren Sie die Daten des zeitgesteuerten Metadatenobjekts, um festzustellen, ob das Objekt einen Sperreintrag oder -ausstieg anzeigt. Bei identifizierten Blackouts rufen Sie die relevanten TVSDK-Elemente auf, um zu Beginn der Blackout-Meldung zu alternativen Inhalten zu wechseln und wieder zum Hauptinhalt zurückzukehren, wenn die Blackout-Meldung beendet ist.

>[!TIP]
>
>Die Schlüssel werden weiterhin aus dem Manifest heruntergeladen, bevor der Inhalt wiedergegeben wird.

Wenn ein Benutzer eine Verbindung zu einem Live-Stream herstellt, nachdem die Sperrfrist abgelaufen ist, und dann zu der Sperrfrist zurückkehrt, wird der Inhalt abgespielt.

>[!IMPORTANT]
>
>Wenn alle Schlüsselanforderungen fehlschlagen, wird beim Analysieren des Manifests ein Fehler ausgegeben. Wenn einige Anforderungen fehlschlagen und einige erfolgreich sind, versucht TVSDK, den Inhalt wiederzugeben. Wenn TVSDK versucht, einen Abschnitt des Inhalts abzuspielen, aber kein gültiger Schlüssel zum Entschlüsseln dieses Inhalts vorhanden ist, wird ein Fehler zurückgegeben.

So behandeln Sie Blackouts in Live-Streams:

1. Richten Sie Ihre App so ein, dass Blackout-Tags erkannt werden, indem Sie Blackout-Tags in einem Live-Stream-Manifest abonnieren.

   TVSDK erkennt keine Blackout-Tags allein. Sie müssen Blackout-Tags abonnieren, um eine Benachrichtigung zu erhalten, wenn die Tags während der Analyse der Manifestdatei gefunden werden.
1. Erstellen Sie Ereignis-Listener für Tags, für die Ihr Player abonniert ist.

   Wenn ein Tag auftritt, das Ihr Player abonniert hat (z. B. ein Blackout-Tag), entweder im Vordergrund (Hauptinhalt) oder im Hintergrund (alternativer Inhalt), löst TVSDK ein `TimedMetadataEvent` aus und erstellt ein `TimedMetadataObject` für das `TimedMetadataEvent`.
1. Implementieren Sie Handler für die zeitgesteuerten Metadaten-Ereignis für den Vordergrund- und den Hintergrund-Stream.

   Rufen Sie in diesen Handlern die Beginns- und Endzeiten für die Sperrfrist von den zeitgesteuerten Metadaten-Ereignis-Objekten ab.
1. Bereiten Sie das `MediaPlayer` für Blackouts vor.

   Wenn das `MediaPlayer` in den Status &quot;VORBEREITT&quot;wechselt, berechnen und bereiten Sie die Sperrbereiche vor und legen Sie sie auf das `MediaPlayer`-Objekt fest.

1. Überprüfen Sie für jedes Update auf die Abspielposition die Liste von `TimedMetadataObjects`.

   Hier erkennt Ihr Spieler den Blackout-Beginn und das Ende und zeichnet die Zeitdauer des Blackout auf, während er eintritt.

1. Erstellen Sie Methoden zum Wechseln von Inhalten am Beginn und am Ende der Sperrfrist.

   Wenn die Sperrfrist Beginn ist, wechseln Sie den Hauptinhalt in den Hintergrund und wechseln Sie zum alternativen Inhalt, um der Hauptstrom zu werden. Rufen Sie weiterhin das ursprüngliche Manifest im Hintergrund ab und analysieren Sie es und suchen Sie nach dem Tag &quot;Blackout End&quot;, damit der Player wieder am ursprünglichen Stream teilnehmen kann, wenn das Blackout beendet wird.

