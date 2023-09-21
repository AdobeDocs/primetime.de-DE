---
description: Einige Anzeigen von Drittanbietern (oder kreative Inhalte) können nicht in den Inhaltsstream HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming über HTTP (DASH) zugeordnet werden, da ihr Videoformat mit HLS/DASH inkompatibel ist. Adobe Primetime-Anzeigeneinfügung und Browser TVSDK können optional versuchen, inkompatible Videos in kompatible m3u8/mpd-Videos neu zu verpacken (transkodieren).
title: Repacken (Transkodieren) inkompatibler Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Repacken (Transkodieren) inkompatibler Anzeigen{#repackage-transcode-incompatible-ads}

Einige Anzeigen von Drittanbietern (oder kreative Inhalte) können nicht in den Inhaltsstream HTTP Live Streaming (HLS)/Dynamic Adaptive Streaming über HTTP (DASH) zugeordnet werden, da ihr Videoformat mit HLS/DASH inkompatibel ist. Adobe Primetime-Anzeigeneinfügung und Browser TVSDK können optional versuchen, inkompatible Videos in kompatible m3u8/mpd-Videos neu zu verpacken (transkodieren).

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Inventarpartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie progressiv herunterladbarem MP4 bereitgestellt.
