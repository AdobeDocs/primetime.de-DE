---
description: Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-description: Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
seo-title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live oder VOD{#identify-whether-the-content-is-live-or-vod} ist.

Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Warten Sie, bis Browser TVSDK ein `AdobePSDK.PSDKEventType.STATUS_CHANGED`-Ereignis mit einem `event.status` von `AdobePSDK.MediaPlayerStatus.PREPARED` auslöst.

   Dieser Schritt stellt sicher, dass die Medienressource erfolgreich geladen wurde.

   >[!IMPORTANT]
   >
   >Wenn Browser TVSDK nicht mindestens den Status `PREPARED` aufweist, wird beim Versuch, die folgenden Methoden aufzurufen, ein `IllegalStateException`-Wert zurückgegeben.

1. Lesen Sie `live` über die `MediaPlayerItem`-Schnittstelle:

   ```js
   player.currentItem.live
   ```

