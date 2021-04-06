---
title: Transkodierung und Normalisierung
description: Transkodierung und Normalisierung
copied-description: true
exl-id: 48d9d971-4b15-4f1b-8740-c21983a3e835
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '92'
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
