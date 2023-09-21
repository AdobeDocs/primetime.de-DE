---
description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
title: Identifizieren, ob der Inhalt live oder VOD ist
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Identifizieren, ob der Inhalt live oder VOD ist{#identify-whether-the-content-is-live-or-vod}

In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Stellen Sie sicher, dass der Player mindestens den Status VORBEREITET aufweist.
1. Bestimmen Sie, ob die `MediaPlayerItem` Inhalt ist live (true) oder VOD (false).

   ```java
   boolean isLive();
   ```
