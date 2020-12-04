---
description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-title: Arbeiten mit Untertiteln
title: Arbeiten mit Untertiteln
uuid: bc069e04-3ea3-4cdf-a8a6-d8aef91ece91
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Arbeiten mit Untertiteln{#work-with-closed-captions}

Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.

Untertitel sind in der Regel in derselben Sprache wie die Audiodaten und zeigen auch Hintergrundgeräusche als Text an. Untertitel sind jedoch in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.

Browser TVSDK unterstützt die Wiedergabe folgender Formate:

* 608 und 708 schließen Untertitel, wenn sie als Teil des Videotransports über HLS als Datenpakete in MPEG-2-Videostreams bereitgestellt werden.
* WebVTT-Untertiteldateien, die aus den in den HLS-Spezifikationen definierten Manifestdateien des M3U8 referenziert werden. Sie sind im Primetime-Player automatisch als Untertitelspuren verfügbar.

Sie können:

* Wählen Sie eine verfügbare Untertitelspur als aktuelle Spur aus und suchen Sie nach Ereignissen, die zusätzliche verfügbare Spuren anzeigen.
* Schalten Sie die Untertitel über die `MediaPlayer`-Schnittstelle ein oder aus (sichtbar oder nicht sichtbar).
* Wählen Sie Stiloptionen, die bestimmen, wie Untertitel von der zugrunde liegenden Video-Engine gerendert werden. Verwenden Sie die `MediaPlayerItem`-Schnittstelle, um Formate wie Schriftart oder Schriftfarbe auszuwählen.

