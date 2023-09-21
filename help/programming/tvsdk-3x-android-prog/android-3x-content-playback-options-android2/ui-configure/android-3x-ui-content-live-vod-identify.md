---
description: Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder Video On Demand (VOD) ist.
title: Identifizieren, ob der Inhalt live oder VOD ist
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---

# Identifizieren, ob der Inhalt live oder VOD ist {#identify-whether-the-content-is-live-or-vod}

Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder Video On Demand (VOD) ist.

1. Stellen Sie sicher, dass sich der Player mindestens in der `PREPARED` state.
1. Bestimmen Sie, ob die `MediaPlayerItem` Inhalt ist live ( `true`) oder VOD ( `false`).

   ```java
   boolean isLive();
   ```
