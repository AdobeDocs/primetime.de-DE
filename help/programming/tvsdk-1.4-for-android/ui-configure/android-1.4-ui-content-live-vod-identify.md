---
description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
uuid: cd71b8d3-259a-48f8-a6ad-02b57da146a7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live oder VOD{#identify-whether-the-content-is-live-or-vod} ist.

In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Stellen Sie sicher, dass der Player mindestens den Status &quot;VORBEREITET&quot;aufweist.
1. Stellen Sie fest, ob der `MediaPlayerItem`-Inhalt live (true) oder VOD (false) ist.

   ```java
   boolean isLive();
   ```

