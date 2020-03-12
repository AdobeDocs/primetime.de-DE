---
description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-description: Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.
seo-title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
title: Wählen Sie eine aktuelle Beschriftungsspur aus den verfügbaren Spuren
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Übersicht {#work-with-closed-captions}

Bei Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton nicht hörbar ist oder der Viewer schwer zu hören ist.

Untertitel sind in der Regel in derselben Sprache wie die Audiodaten und zeigen auch Hintergrundgeräusche als Text an. Untertitel sind jedoch in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.

TVSDK unterstützt das Rendering folgender Formate:

* 608 und 708 schließen Untertitel, wenn sie als Teil des Videotransports über HLS als Datenpakete in MPEG-2-Videostreams bereitgestellt werden.
* WebVTT-Untertiteldateien, die aus den in den HLS-Spezifikationen definierten Manifestdateien des M3U8 referenziert werden. Sie sind im Primetime-Player automatisch als Untertitelspuren verfügbar.

Sie können:

* Wählen Sie eine verfügbare Untertitelspur als aktuelle Spur aus und suchen Sie nach Ereignissen, die zusätzliche verfügbare Spuren anzeigen.
* Schalten Sie die Untertitel über die `MediaPlayer` Benutzeroberfläche ein oder aus (sichtbar oder nicht sichtbar).
* Wählen Sie Stiloptionen, die bestimmen, wie Untertitel von der zugrunde liegenden Video-Engine gerendert werden. Verwenden Sie die `MediaPlayerItem` Oberfläche, um Formate wie Schriftart oder Schriftfarbe auszuwählen.
