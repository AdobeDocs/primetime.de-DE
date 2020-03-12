---
description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen "Verzögertes Laden von Werbeanzeigen"und "Verzögertes Auflösen von Werbeanzeigen"können diese Startverzögerung verringern. Lazy Ad Resolving hat sich in der Version 3.0 erheblich geändert. Beim Laden von Lazy Ad vor 3.0 wurde die Anzeigenauflösung in zwei Schritte unterteilt, wobei nur Pre-Roll-Anzeigen vor dem Status "VORBEREITET"und Mid-Roll- und Post-Roll nach dem Status "VORBEREITT"aufgelöst wurden. Dies wurde geändert, und die Werbeunterbrechungen werden nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.
keywords: Lazy;Ad resolving;Ad loading
seo-description: Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen "Verzögertes Laden von Werbeanzeigen"und "Verzögertes Auflösen von Werbeanzeigen"können diese Startverzögerung verringern. Lazy Ad Resolving hat sich in der Version 3.0 erheblich geändert. Beim Laden von Lazy Ad vor 3.0 wurde die Anzeigenauflösung in zwei Schritte unterteilt, wobei nur Pre-Roll-Anzeigen vor dem Status "VORBEREITET"und Mid-Roll- und Post-Roll nach dem Status "VORBEREITT"aufgelöst wurden. Dies wurde geändert, und die Werbeunterbrechungen werden nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.
seo-title: Just-in-time-Anzeigenauflösung
title: Just-in-time-Anzeigenauflösung
uuid: 77028f6e-7e53-45d1-bcc0-54f8224d6d18
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht {#just-in-time-ad-resolving-overview}

Das Auflösen und Laden von Anzeigen kann für einen Benutzer, der auf die Wiedergabe auf dem Beginn wartet, zu einer inakzeptablen Verzögerung führen. Die Funktionen &quot;Verzögertes Laden von Werbeanzeigen&quot;und &quot;Verzögertes Auflösen von Werbeanzeigen&quot;können diese Startverzögerung verringern. Lazy Ad Resolving hat sich in der Version 3.0 erheblich geändert. Beim Laden von Lazy Ad vor 3.0 wurde die Anzeigenauflösung in zwei Schritte unterteilt, wobei nur Pre-Roll-Anzeigen vor dem Status &quot;VORBEREITET&quot;und Mid-Roll- und Post-Roll nach dem Status &quot;VORBEREITT&quot;aufgelöst wurden. Dies wurde geändert, und die Werbeunterbrechungen werden nun in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.

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
   1. TVSDK löst jeden der verbleibenden Werbeunterbrechungen einzeln auf Grundlage der folgenden Berechnung auf:

      `AdvertisingMetadata::getDelayAdLoadingTolerance() + PlayBufferTime::playBufferTime + the value defined in EXT-X-TARGETDURATION`

      Standardmäßig beträgt die Dauer für Inhalte mit einer Zielgruppe von 6 Sekunden 5,0 + 30,0 + 6,0 Sekunden (41 Sekunden)

   1. Tritt innerhalb von 10 Sekunden nach der Position des Beginns ein Werbeumbruch auf, wird dieser zusammen mit Pre-Roll-Anzeigen vor dem Status &quot;VORBEREITT&quot;aufgelöst.

>[!IMPORTANT]
>
>**Faktoren, die bei der Auflösung von Lazy Ad zu berücksichtigen sind:** >
>* Lazy Ad Resolving wird nur für VOD-Streams mit den Modi SERVER_MAP und MANIFEST_CUES unterstützt.
>* Die verzögerte Anzeigenauflösung ist nicht standardmäßig aktiviert. Wenn diese Option deaktiviert ist, werden alle Anzeigen bei VOD-Streams aufgelöst, bevor Beginn wiedergegeben werden.
>* Die verzögerte Anzeigenauflösung ist nicht mit der Funktion &quot;Sofortiges Anzeigen&quot;kompatibel. Weitere Informationen zu &quot;Sofort ein&quot;finden Sie unter Sofort ein.
>* Bei der Auflösen von verzögerter Anzeige während der Suche über eine Werbeunterbrechung wird die nächste Werbeunterbrechung an der Suchposition während der Suche aufgelöst.
>* Wenn bei verzögerter Anzeigenauflösung mehrere Werbeunterbrechungen gleichzeitig vorhanden sind (VMAP), werden sie gleichzeitig aufgelöst.
>* Es wird nicht empfohlen, den Wert *setDelayAdLoadingTolerance() *unter den Standardwert (5 Sekunden) zu verringern. Dies könnte dazu führen, dass der Player unnötig &quot;puffert&quot;.
>* Die verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.
>* Lazy Ad Resolving wird derzeit mit dem Auditude-Plugin unterstützt. Es wird empfohlen, ** setDelayAdLoadingnicht auf true festzulegen, wenn Sie einen benutzerdefinierten Auflöser verwenden.
>


