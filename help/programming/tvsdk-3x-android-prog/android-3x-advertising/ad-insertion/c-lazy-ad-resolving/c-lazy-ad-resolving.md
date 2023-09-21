---
description: Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktionen "Lazy Ad Loading"und "Lazy Ad Resolving"können diese Startverzögerung reduzieren. Die Lazy Ad Resolving hat sich in Version 3.0 erheblich geändert. Beim Laden verzögerter Anzeigen vor 3.0 wurde die Anzeigenauflösung in zwei Schritte unterteilt, wobei nur Pre-Roll-Anzeigen vor dem Status VORBEREITT und Mid-Roll und Post-Roll nach dem Status VORBEREITT aufgelöst wurden. Dies hat sich geändert, und die Werbeunterbrechungen werden jetzt in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.
keywords: Verzögert; auflösen von Anzeigen; Laden von Anzeigen
title: Just-in-time-Anzeigenauflösung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# Übersicht {#just-in-time-ad-resolving-overview}

Das Auflösen von Anzeigen und Laden von Anzeigen kann zu einer inakzeptablen Verzögerung für einen Benutzer führen, der auf den Start der Wiedergabe wartet. Die Funktionen &quot;Lazy Ad Loading&quot;und &quot;Lazy Ad Resolving&quot;können diese Startverzögerung reduzieren. Die Lazy Ad Resolving hat sich in Version 3.0 erheblich geändert. Beim Laden verzögerter Anzeigen vor 3.0 wurde die Anzeigenauflösung in zwei Schritte unterteilt, wobei nur Pre-Roll-Anzeigen vor dem Status VORBEREITT und Mid-Roll und Post-Roll nach dem Status VORBEREITT aufgelöst wurden. Dies hat sich geändert, und die Werbeunterbrechungen werden jetzt in einem bestimmten Intervall vor der Position der Werbeunterbrechung aufgelöst.

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
   1. TVSDK löst die verbleibenden Werbeunterbrechungen einzeln auf Grundlage der folgenden Berechnung auf:

      `AdvertisingMetadata::getDelayAdLoadingTolerance() + PlayBufferTime::playBufferTime + the value defined in EXT-X-TARGETDURATION`

      Standardmäßig beträgt für Inhalte mit einer Target-Dauer von 6 Sekunden dieser Wert 5,0 + 30,0 + 6,0 Sekunden (41 Sekunden)

   1. Wenn innerhalb von 10 Sekunden nach der Startposition eine Werbeunterbrechung auftritt, wird diese zusammen mit Pre-Roll-Anzeigen vor dem Status VORBEREITT aufgelöst.

>[!IMPORTANT]
>
>**Faktoren, die bei der verzögerten Anzeigenauflösung berücksichtigt werden sollten:**
>
>* Lazy Ad Resolving wird nur für VOD-Streams mit den Modi SERVER_MAP und MANIFEST_CUES unterstützt.
>* Die verzögerte Anzeigenauflösung ist standardmäßig nicht aktiviert. Wenn diese Option deaktiviert ist, werden alle Anzeigen in VOD-Streams vor dem Start der Wiedergabe aufgelöst.
>* Die verzögerte Anzeigenauflösung ist mit der Funktion &quot;Instant On&quot;nicht kompatibel. Weitere Informationen zu &quot;Sofort ein&quot;finden Sie unter Sofort ein.
>* Bei verzögerter Anzeigenauflösung wird bei der Suche über eine Werbeunterbrechung die nächstliegende Werbeunterbrechung zur Suchposition während der Suche aufgelöst.
>* Bei verzögerter Anzeigenauflösung werden mehrere Werbeunterbrechungen gleichzeitig (VMAP) aufgelöst.
>* Es wird nicht empfohlen, den Wert von *setDelayAdLoadingTolerance() *unter den Standardwert (5 Sekunden) zu reduzieren. Dies könnte dazu führen, dass der Player unnötig &quot;puffert&quot;.
>* Die verzögerte Anzeigenauflösung wirkt sich nicht auf Pre-Roll-Anzeigen aus.
>* Lazy Ad Resolving wird derzeit mit dem Auditude-Plugin unterstützt. Es wird empfohlen, keine *setDelayAdLoading* auf &quot;true&quot;fest, wenn Sie einen benutzerdefinierten Resolver verwenden.
>
