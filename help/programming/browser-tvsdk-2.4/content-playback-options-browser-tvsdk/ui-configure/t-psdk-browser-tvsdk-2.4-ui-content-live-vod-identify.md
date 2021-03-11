---
description: Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.
title: Identifizieren Sie, ob der Inhalt live oder VOD ist.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---


# Identifizieren Sie, ob der Inhalt live oder VOD{#identify-whether-the-content-is-live-or-vod} ist.

Möglicherweise müssen Sie wissen, ob der Medieninhalt live oder VOD ist.

1. Warten Sie, bis Browser TVSDK ein `AdobePSDK.PSDKEventType.STATUS_CHANGED`-Ereignis mit einem `event.status` von `AdobePSDK.MediaPlayerStatus.PREPARED` Trigger.

   Dieser Schritt stellt sicher, dass die Medienressource erfolgreich geladen wurde.

   >[!IMPORTANT]
   >
   >Wenn Browser TVSDK nicht mindestens den Status `PREPARED` aufweist, wird beim Versuch, die folgenden Methoden aufzurufen, ein `IllegalStateException`-Wert ausgegeben.

1. Lesen Sie `live` über die `MediaPlayerItem`-Schnittstelle:

   ```js
   player.currentItem.live
   ```

