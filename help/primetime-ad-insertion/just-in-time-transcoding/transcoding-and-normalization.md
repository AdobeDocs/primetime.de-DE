---
title: Transkodierung und Normalisierung
description: null
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# Transkodierung und Normalisierung {#transcoding-and-normalization}

Primetime Ad Insertion versucht, eine konsistente Anzeige über Inhalte und Anzeigen hinweg sicherzustellen, indem versucht wird, eine Übereinstimmung zu finden:

1. Quellstream-Codecs und Bit-Raten bei gleichzeitiger Auswahl der kreativsten Qualität/Bitrate beim Transkodieren

1. Quellstream-Fragmentgrößen (HLS/#EXT-X-TARGETDURATION)

1. Bevorzugte kreative Formate für die Transkodierung

1. Automatische Audio-Auslagerung, um eine einheitliche dB-Stufe für alle Werbeinhalte zu gewährleisten.

>[!NOTE]
>
>HLS-Assets, die durch die Just-in-time-Transkodierung von Primetime-Ad Insertion generiert wurden, produzieren HLS-Assets der Version 3, unabhängig davon, welche HLS-Version im Inhalt definiert ist.