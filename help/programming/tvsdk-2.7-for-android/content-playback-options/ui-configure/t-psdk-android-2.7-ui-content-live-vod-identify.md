---
description: Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.
seo-description: Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.
seo-title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
uuid: d49315ee-8cec-4b79-adbd-a49c2a527424
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live ist oder VOD {#identify-whether-the-content-is-live-or-vod}

Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.

1. Stellen Sie sicher, dass sich der Player mindestens im Status `PREPARED` befindet.
1. Stellen Sie fest, ob der Inhalt von `MediaPlayerItem` live ( `true`) oder VOD ( `false`) ist.

   ```java
   boolean isLive();
   ```
