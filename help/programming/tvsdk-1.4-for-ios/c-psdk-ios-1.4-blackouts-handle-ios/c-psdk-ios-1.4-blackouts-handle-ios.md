---
description: TVSDK verarbeitet Blackouts in Live-Video-Streams und bietet alternativen Inhalt während einer Blackout-Phase.
seo-description: TVSDK verarbeitet Blackouts in Live-Video-Streams und bietet alternativen Inhalt während einer Blackout-Phase.
seo-title: Umgang mit Stromausfällen in Live-Streams
title: Umgang mit Stromausfällen in Live-Streams
uuid: 1f70a272-bc77-4d41-a999-b076cb42ac5e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Umgang mit Stromausfällen in Live-Streams{#handle-blackouts-in-live-streams}

TVSDK verarbeitet Blackouts in Live-Video-Streams und bietet alternativen Inhalt während einer Blackout-Phase.

Der häufigste Anwendungsfall im Zusammenhang mit einem Blackout beim Programmieren ist der Fall, wenn Ihre Player-App Benutzern, die nicht zum Anzeigen des Hauptstreams berechtigt sind, alternativen Inhalt bereitstellt. Diese App kann TVSDK verwenden, um den Beginn und das Ende der Blackout-Phase zu bestimmen. Auf diese Weise kann zu Beginn der Blackout-Phase die Wiedergabe vom Hauptstrom zu einem alternativen Stream wechseln und dann zum Hauptstrom wechseln, wenn die Blackout-Phase vorüber ist.

So implementieren Sie die Lösung für diesen Anwendungsfall:

1. Richten Sie Ihre App so ein, dass sie Blackout-Tags in einem Live-Stream-Manifest abonniert.

   TVSDK kennt keine Blackout-Tags, aber es ermöglicht Ihrer App das Abonnieren von Benachrichtigungen, wenn beim Analysieren von Manifestdateien bestimmte Tags gefunden werden.
1. Hinzufügen einen Benachrichtigungs-Listener für `PTTimedMetadataChangedNotification`.

   Diese Benachrichtigung wird jedes Mal ausgelöst, wenn ein abonniertes Tag im Manifest analysiert wird und ein neuer aus dem Tag vorbereitet `PTTimedMetadata` wird.

1. Implementieren Sie eine Listener-Methode, z. B. `onMediaPlayerSubscribedTagIdentified`für `PTTimedMetadata` Objekte im Vordergrund.

1. Verwenden Sie bei jeder Aktualisierung während der Wiedergabe den `PTMediaPlayerTimeChangeNotification` Listener, um `PTTimedMetadata` Objekte zu verarbeiten.

1. Hinzufügen den `PTTimedMetadata` Handler.

   Mit diesem Handler können Sie zu alternativen Inhalten wechseln und zum Hauptinhalt zurückkehren, wie vom `PTTimedMetadata` Objekt und seiner Wiedergabezeit angegeben.

1. Verwenden Sie `onSubscribedTagInBackground` zum Implementieren der Listener-Methode für `PTTimedMetadata` Objekte im Hintergrund.

   Diese Methode überwacht das Timing im Hintergrundstream, was Ihnen hilft, festzustellen, wann Sie von alternativen Inhalten zurück zum Hauptinhalt wechseln können.

1. Implementieren Sie eine Listener-Methode für Hintergrundfehler.
1. Wenn sich der Blackout-Bereich im DVR im Wiedergabestream befindet, aktualisieren Sie die nicht suchbaren Bereiche.

   In den folgenden Fällen muss die Anwendung den nicht suchbaren Bereich im DVR einstellen:

   * Bei der Verbindung zum Hauptstrom, wenn sich ein Blackout im DVR befindet.
   * Beim Zurückschalten zum Hauptinhalt vom alternativen Inhalt.

