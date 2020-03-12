---
description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
uuid: 4d514c46-a1d0-4721-a423-92108126e37e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Identifizieren Sie, ob der Inhalt live oder VOD ist.{#identify-whether-the-content-is-live-or-vod}

In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Stellen Sie sicher, dass der Player mindestens den Status INITIALIZED aufweist.
1. Stellen Sie fest, ob der `MediaPlayerItem` Inhalt live (true) oder VOD (false) ist.

   ```
   function get isLive():Boolean;
   ```

