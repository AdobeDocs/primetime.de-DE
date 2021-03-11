---
description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
title: Arbeiten mit Untertiteln
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Übersicht {#work-with-closed-captions-overview}

Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.

Untertitel sind in der Regel in derselben Sprache wie die Audiodaten und zeigen auch Hintergrundgeräusche als Text an. Untertitel sind jedoch in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.

TVSDK unterstützt das Rendering folgender Formate:

* 608 und 708 schließen Untertitel, wenn sie als Teil des Videotransports über HLS als Datenpakete in MPEG-2-Videostreams bereitgestellt werden.
* WebVTT-Untertiteldateien, die aus den in den HLS-Spezifikationen definierten Manifestdateien des M3U8 referenziert werden.

   Diese Dateien sind automatisch als Untertitel-Tracks im Primetime-Player verfügbar.

Sie haben folgende Möglichkeiten:

* Wählen Sie eine verfügbare Untertitelspur als aktuelle Spur aus und suchen Sie nach Ereignissen, die zusätzliche verfügbare Spuren anzeigen.
* Schalten Sie die Untertitel über die `MediaPlayer`-Schnittstelle ein (sichtbar) oder aus (nicht sichtbar).
* Wählen Sie Stiloptionen, die bestimmen, wie Untertitel von der zugrunde liegenden Video-Engine gerendert werden.

   Verwenden Sie die `MediaPlayerItem`-Schnittstelle, um Formate wie Schriftart oder Schriftfarbe auszuwählen.

