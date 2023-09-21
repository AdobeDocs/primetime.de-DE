---
description: Bei verdeckten Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton unhörbar oder der Viewer schwerhörig ist.
title: Arbeiten mit geschlossenen Untertiteln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Übersicht {#work-with-closed-captions-overview}

Bei verdeckten Untertiteln wird der Audioteil eines Videos als Text auf dem Bildschirm angezeigt, wenn der Ton unhörbar oder der Viewer schwerhörig ist.

Geschlossene Untertitel sind in der Regel in derselben Sprache wie das Audio und zeigen auch Hintergrundgeräusche als Text an, Untertitel sind jedoch in der Regel in einer anderen Sprache und enthalten keine Hintergrundgeräusche.

TVSDK unterstützt das Rendern dieser Formate:

* 608 und 708 verdeckte Untertitel, wenn sie als Teil des Videotransport-Streams über HLS als Datenpakete in MPEG-2-Videostreams bereitgestellt werden.
* WebVTT-Untertiteldateien, die aus den M3U8-Manifestdateien referenziert werden, wie in den HLS-Spezifikationen definiert.

  Diese Dateien sind automatisch als Untertitelspuren im Primetime-Player verfügbar.

Sie können Folgendes tun:

* Wählen Sie einen verfügbaren Untertitelpfad als aktuellen Track aus und überwachen Sie auf Ereignisse, die zusätzliche verfügbare Tracks anzeigen.
* Schalten Sie die verdeckten Untertitel ein (sichtbar) oder aus (nicht sichtbar), indem Sie die `MediaPlayer` -Schnittstelle.
* Wählen Sie Stiloptionen aus, die bestimmen, wie geschlossene Untertitel von der zugrunde liegenden Video-Engine gerendert werden.

  Verwenden Sie die `MediaPlayerItem` -Schnittstelle, um Formate wie Schriftart oder Schriftfarbe auszuwählen.
