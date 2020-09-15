---
description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen "Verzögertes Laden von Werbeanzeigen"und "Verzögertes Auflösen von Werbeanzeigen"können diese Startverzögerung verringern.
keywords: Lazy;Ad resolving;Ad loading
seo-description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen "Verzögertes Laden von Werbeanzeigen"und "Verzögertes Auflösen von Werbeanzeigen"können diese Startverzögerung verringern.
seo-title: Verzögerte und gelöste Anzeige
title: Verzögerte und gelöste Anzeige
uuid: cf9ba788-b83f-43aa-94c4-db391d92a77b
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Übersicht {#lazy-ad-resolving}

Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen &quot;Verzögertes Laden von Werbeanzeigen&quot;und &quot;Verzögertes Auflösen von Werbeanzeigen&quot;können diese Startverzögerung verringern.

* Grundlegender Prozess zum Auflösen und Laden von Anzeigen:

   1. TVSDK lädt ein Manifest (Playlist) herunter und löst *alle Anzeigen* auf.
   1. TVSDK *lädt* alle Anzeigen und platziert sie auf der Zeitschiene.
   1. TVSDK verschiebt den Player in den Status &quot;VORBEREITT&quot;, und die Wiedergabe des Inhalts beginnt.

   Der Player verwendet die URLs im Manifest, um den Anzeigeninhalt (kreative Elemente) abzurufen, stellt sicher, dass der Anzeigeninhalt in einem Format vorliegt, das TVSDK wiedergeben kann, und TVSDK platziert die Anzeigen auf der Zeitleiste. Dieser grundlegende Prozess des Auflösens und Ladens von Anzeigen kann zu einer unannehmbar langen Verzögerung für Benutzer führen, die auf die Wiedergabe ihres Inhalts warten, insbesondere wenn das Manifest mehrere Anzeigen-URLs enthält.

* *Verzögertes Laden* von Anzeigen:

   1. TVSDK lädt eine Playlist herunter und *löst* alle Anzeigen.
   1. TVSDK *lädt* Pre-Roll-Anzeigen, verschiebt den Player in den Status &quot;VORBEREITT&quot;und die Inhaltswiedergabe beginnt.
   1. TVSDK *lädt* die verbleibenden Anzeigen und setzt sie während der Wiedergabe auf die Zeitleiste.

   Diese Funktion verbessert den grundlegenden Prozess, indem der Player in den Status &quot;VORBEREITT&quot;versetzt wird, bevor alle Anzeigen geladen werden.

* *Lazy Ad Resolving*:

   1. TVSDK lädt die Wiedergabeliste herunter.
   1. TVSDK löst und lädt alle Pre-Roll-Anzeigen, verschiebt den Player in den Status &quot;VORBEREITT&quot;und die Inhaltswiedergabe beginnt.
   1. TVSDK löst und lädt die verbleibenden Anzeigen und setzt sie bei der Wiedergabe auf die Zeitleiste.

   Die Lazy Ad Resolving-Funktion baut auf Lazy Ad Loading auf, um einen noch schnelleren Beginn zu ermöglichen. Nachdem TVSDK Pre-Roll-Anzeigen platziert hat, wird der Player in den Status &quot;VORBEREITET&quot;verschoben und löst dann zusätzliche Anzeigen auf und platziert sie auf der Zeitschiene.

>[!IMPORTANT]
>
>Faktoren, die bei der Auflösung von Lazy Ad zu berücksichtigen sind:
>
>* Die verzögerte Anzeigenauflösung ist standardmäßig aktiviert. Wenn Sie sie deaktivieren, werden alle Anzeigen vor dem Beginn der Wiedergabe aufgelöst.
>* Die verzögerte Anzeigenauflösung erlaubt keine Suche oder Trickplay, bis alle Anzeigen aufgelöst sind:

   >
   >    
   * Der Spieler muss auf das `kEventAdResolutionComplete` Ereignis warten, bevor er die Suche oder das Trick-Spiel erlaubt.
   >    * Wenn der Benutzer versucht, Vorgänge zum Suchen oder Tricken von Wiedergabe auszuführen, während Anzeigen weiterhin aufgelöst werden, gibt TVSDK den `kECLazyAdResolutionInProgress` Fehler aus.
   >    * Bei Bedarf sollte der Player die Scrubbing-Leiste aktualisieren, *nachdem* das `kEventAdResolutionComplete` Ereignis empfangen wurde.
>
>* Lazy Ad Resolving ist nur für VOD gedacht. Es funktioniert nicht mit LIVE-Streams.
>* Die verzögerte Anzeigenauflösung ist nicht mit der Funktion *Sofortiges* kompatibel.

>
>  

Weitere Informationen zu &quot;Sofort ein&quot;finden Sie unter Sofort-on .
>
>* Beim Auflösen von verzögerter Anzeige beginnt die Wiedergabe zwar viel schneller, aber wenn in den ersten 60 Sekunden der Wiedergabe ein Werbeunterbrechung auftritt, wird dieser möglicherweise nicht behoben.
>* Eine verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.