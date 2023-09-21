---
title: Transkodierung und Normalisierung
description: Transkodierung und Normalisierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Transkodierung und Normalisierung {#transcoding-and-normalization}

Primetime Ad Insertion versucht, ein konsistentes Anzeigeerlebnis über Inhalte und Anzeigen hinweg sicherzustellen, indem versucht wird, eine Übereinstimmung zu finden:

1. Quell-Stream-Codecs und Bitraten, während bei der Transkodierung immer die kreativste Qualität/Bitrate ausgewählt wird

1. Größe von Quell-Stream-Fragmenten (HLS/#EXT-X-TARGETDURATION)

1. Bevorzugte kreative Formate für die Transkodierung

1. Automatische Audioebene, um eine konsistente dB-Ebene für alle Anzeigenkreativen sicherzustellen.

>[!NOTE]
>
>HLS-Assets, die von der Just-in-time-Transkodierung der Primetime-Ad Insertion generiert werden, produzieren HLS-Assets der Version 3, unabhängig davon, welche HLS-Version im Inhalt definiert ist.
