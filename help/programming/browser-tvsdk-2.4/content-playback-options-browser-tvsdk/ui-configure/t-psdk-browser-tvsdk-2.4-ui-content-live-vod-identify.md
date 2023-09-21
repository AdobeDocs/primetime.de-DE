---
description: Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
title: Identifizieren, ob der Inhalt live oder VOD ist
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---

# Identifizieren, ob der Inhalt live oder VOD ist{#identify-whether-the-content-is-live-or-vod}

Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Warten Sie, bis das Browser TVSDK einen Trigger und ein `AdobePSDK.PSDKEventType.STATUS_CHANGED` -Ereignis mit einer `event.status` von `AdobePSDK.MediaPlayerStatus.PREPARED`.

   Dieser Schritt stellt sicher, dass die Medienressource erfolgreich geladen wurde.

   >[!IMPORTANT]
   >
   >Wenn Browser TVSDK nicht mindestens in der `PREPARED` state, der versucht, die folgenden Methoden aufzurufen, gibt eine `IllegalStateException`.

1. Lesen `live` aus dem `MediaPlayerItem` -Schnittstelle:

   ```js
   player.currentItem.live
   ```
