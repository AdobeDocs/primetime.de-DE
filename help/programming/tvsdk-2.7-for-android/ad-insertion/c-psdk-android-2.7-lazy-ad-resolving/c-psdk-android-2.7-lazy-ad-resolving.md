---
description: Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktionen "Lazy Ad Loading"und "Lazy Ad Resolving"können diese Startverzögerung reduzieren.
keywords: Verzögert; auflösen von Anzeigen; Laden von Anzeigen
title: Verzögerte Anzeigenauflösung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Übersicht {#lazy-ad-resolving}

Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktionen &quot;Lazy Ad Loading&quot;und &quot;Lazy Ad Resolving&quot;können diese Startverzögerung reduzieren.

* Grundlegender Prozess zur Anzeigenauflösung und zum Laden:

   1. TVSDK lädt ein Manifest (Wiedergabeliste) herunter und *auflöst* alle Anzeigen.
   1. TVSDK *lädt* alle Anzeigen und platzieren sie auf der Timeline.
   1. TVSDK verschiebt den Player in den Status VORBEREITT , und die Wiedergabe des Inhalts beginnt.

  Der Player verwendet die URLs im Manifest, um den Anzeigeninhalt (kreative Inhalte) zu erhalten, stellt sicher, dass der Anzeigeninhalt in einem Format vorliegt, das TVSDK wiedergeben kann, und TVSDK platziert die Anzeigen auf der Timeline. Dieser grundlegende Prozess der Auflösung und des Ladens von Anzeigen kann dazu führen, dass ein Benutzer, der darauf wartet, seinen Inhalt wiederzugeben, unannehmbar lange verzögert ist, insbesondere wenn das Manifest mehrere Anzeigen-URLs enthält.

* *Lazy Ad Loading*:

   1. TVSDK lädt eine Wiedergabeliste herunter und *auflöst* alle Anzeigen.
   1. TVSDK *lädt* Pre-Roll-Anzeigen, verschiebt den Player in den Status VORBEREITET und die Inhaltswiedergabe beginnt.
   1. TVSDK *lädt* die verbleibenden Anzeigen und setzt sie bei der Wiedergabe auf die Timeline.

  Diese Funktion verbessert den grundlegenden Prozess, indem der Player vor dem Laden aller Anzeigen in den Status VORBEREITET versetzt wird.

* *Auflösung verzögerter Anzeigen*:

   1. TVSDK lädt die Wiedergabeliste herunter.
   1. TVSDK löst alle Pre-Roll-Anzeigen auf und lädt sie, verschiebt den Player in den Status VORBEREITT und die Inhaltswiedergabe beginnt.
   1. TVSDK löst die verbleibenden Anzeigen auf und lädt sie, sobald die Wiedergabe erfolgt, auf die Timeline.

  Die Lazy Ad Resolving-Builds auf &quot;Lazy Ad Loading&quot;, um einen noch schnelleren Start zu ermöglichen. Nachdem TVSDK Pre-Roll-Anzeigen platziert hat, wechselt der Player in den Status VORBEREITT , löst dann zusätzliche Anzeigen auf und platziert sie auf der Timeline.

>[!IMPORTANT]
>
>Faktoren, die bei der verzögerten Anzeigenauflösung berücksichtigt werden sollten:
>
>* Die verzögerte Anzeigenauflösung ist standardmäßig aktiviert. Wenn Sie sie deaktivieren, werden alle Anzeigen vor dem Start der Wiedergabe aufgelöst.
>* Die verzögerte Anzeigenauflösung erlaubt keine Suche oder Trickplay, bis alle Anzeigen aufgelöst wurden:
>
>    * Der Player muss auf die `kEventAdResolutionComplete` -Ereignis, bevor Sie die Suche oder das Tricken der Wiedergabe zulassen.
>    * Wenn der Benutzer versucht, Play-Vorgänge auszuführen, während Anzeigen aufgelöst werden, gibt TVSDK die `kECLazyAdResolutionInProgress` Fehler.
>    * Bei Bedarf sollte der Player die Scrubbing-Leiste aktualisieren. *after* die `kEventAdResolutionComplete` -Ereignis.
>
>* Die verzögerte Anzeigenauflösung ist nur für VOD vorgesehen. Es funktioniert nicht mit LIVE-Streams.
>* Die verzögerte Anzeigenauflösung ist nicht mit der *Sofort aktiviert* Funktion.
>
>  Weitere Informationen zu Instant On finden Sie unter Instant On .
>
>* Während die verzögerte Anzeigenauflösung dazu führt, dass die Wiedergabe viel schneller startet, wird sie möglicherweise nicht behoben, wenn in den ersten 60 Sekunden der Wiedergabe eine Werbeunterbrechung auftritt.
>* Eine verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.
