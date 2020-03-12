---
description: Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.
seo-description: Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.
seo-title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
uuid: e6a66104-97fb-438a-8356-e21f94058c85
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Identifizieren Sie, ob der Inhalt live oder VOD ist. {#identify-whether-the-content-is-live-or-vod}

Möglicherweise müssen Sie wissen, ob es sich bei den Medieninhalten um Live- oder Video-On-Demand-Videos (VOD) handelt.

1. Stellen Sie sicher, dass sich der Player mindestens im `PREPARED` Status befindet.
1. Stellen Sie fest, ob der `MediaPlayerItem` Inhalt live ( `true`) oder VOD ( `false`) ist.

   ```java
   boolean isLive();
   ```
