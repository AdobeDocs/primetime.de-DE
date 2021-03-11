---
description: Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live ist oder VOD {#identify-whether-the-content-is-live-or-vod}

Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.

1. Stellen Sie sicher, dass sich der Player mindestens im Status `PREPARED` befindet.
1. Stellen Sie fest, ob der Inhalt von `MediaPlayerItem` live ( `true`) oder VOD ( `false`) ist.

   ```java
   boolean isLive();
   ```
