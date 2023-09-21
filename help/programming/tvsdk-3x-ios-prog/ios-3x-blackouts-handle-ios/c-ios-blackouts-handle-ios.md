---
description: TVSDK behandelt Blackouts in Live-Video-Streams und bietet alternative Inhalte während einer Blackout-Phase.
title: Umgang mit Blackouts
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Umgang mit Blackouts {#handle-blackouts}

TVSDK behandelt Blackouts in Live-Video-Streams und bietet alternative Inhalte während einer Blackout-Phase.

Der häufigste Anwendungsfall, der mit einem Programmier-Blackout verbunden ist, besteht darin, dass Ihre Player-App Benutzern, die nicht zum Anzeigen des Hauptstreams berechtigt sind, alternative Inhalte bereitstellt. Diese App kann TVSDK verwenden, um den Anfang und das Ende der Blackout-Phase zu bestimmen. Auf diese Weise kann die Wiedergabe zu Beginn der Blackout-Phase vom Hauptstrom zu einem alternativen Stream wechseln und dann wieder zum Hauptstrom wechseln, wenn die Blackout-Phase vorüber ist.

So implementieren Sie die Lösung für diesen Anwendungsfall:

1. Richten Sie Ihre App so ein, dass sie Blackout-Tags in einem Live-Stream-Manifest abonniert.

   TVSDK kennt keine Blackout-Tags, aber es ermöglicht Ihrer App, Benachrichtigungen zu abonnieren, wenn beim Analysieren von Manifestdateien bestimmte Tags auftreten.
1. Hinzufügen eines Benachrichtigungs-Listeners für `PTTimedMetadataChangedNotification`.

   Diese Benachrichtigung wird jedes Mal gesendet, wenn ein abonniertes Tag im Manifest geparst wird, und eine neue `PTTimedMetadata` ist darauf vorbereitet.

1. Implementieren einer Listener-Methode, z. B. `onMediaPlayerSubscribedTagIdentified`, für `PTTimedMetadata` Objekte im Vordergrund.

1. Jedes Mal, wenn während der Wiedergabe ein Update erfolgt, verwenden Sie die `PTMediaPlayerTimeChangeNotification` Listener zum Verarbeiten `PTTimedMetadata` Objekte.

1. Fügen Sie die `PTTimedMetadata` Handler.

   Mit diesem Handler können Sie zu alternativen Inhalten wechseln und zum Hauptinhalt zurückkehren, wie durch die Variable `PTTimedMetadata` -Objekt und dessen Wiedergabedauer.

1. Verwendung `onSubscribedTagInBackground` , um die Listener-Methode für `PTTimedMetadata` Objekte im Hintergrund.

   Diese Methode überwacht die Timing-Funktion im Hintergrund-Stream, mit der Sie feststellen können, wann Sie von alternativen Inhalten zurück zum Hauptinhalt wechseln können.

1. Implementieren Sie eine Listener-Methode für Hintergrundfehler.
1. Wenn sich der Blackout-Bereich im DVR im Wiedergabestream befindet, aktualisieren Sie die nicht suchbaren Bereiche.

   In den folgenden Fällen muss Ihre Anwendung den nicht suchbaren Bereich im DVR festlegen:

   * Beim Beitritt zum Hauptstrom, wenn ein Stromausfall in der DVR auftritt.
   * Beim Wechsel zum Hauptinhalt vom alternativen Inhalt
