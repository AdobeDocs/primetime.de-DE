---
description: In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live oder VOD{#identify-whether-the-content-is-live-or-vod} ist.

In einigen Fällen müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Stellen Sie sicher, dass der Player mindestens den Status INITIALIZED aufweist.
1. Stellen Sie fest, ob der Inhalt von `MediaPlayerItem` live (true) oder VOD (false) ist.

   ```
   function get isLive():Boolean;
   ```

