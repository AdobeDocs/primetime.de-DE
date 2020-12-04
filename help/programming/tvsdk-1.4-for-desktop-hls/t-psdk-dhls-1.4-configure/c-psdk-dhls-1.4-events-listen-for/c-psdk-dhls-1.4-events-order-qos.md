---
description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der QoS-Statistiken beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.
seo-description: TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der QoS-Statistiken beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.
seo-title: QoS-Ereignis
title: QoS-Ereignis
uuid: e6ba1e9b-435b-480d-bea9-bff41b4e0b21
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# QoS-Ereignis{#qos-events}

TVSDK sendet Servicequalitäts-(QoS-)Ereignis, um Ihre Anwendung über Ereignis zu informieren, die die Berechnung der QoS-Statistiken beeinflussen könnten, wie z.B. Pufferung und Suche von Ereignissen.

Das folgende Beispiel zeigt eine typische Progression dieser Ereignis:

```
// For buffering 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_BEGIN, onBufferingBegin); 
private function onBufferingBegin(event:BufferEvent):void { ... } 
 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_END, onBufferingCompleted); 
private function onBufferingCompleted(event:BufferEvent):void { ... } 
 
// For seeking 
mediaPlayer.addEventListener(SeekEvent.SEEK_BEGIN, onSeekBegin); 
private function onSeekBegin(event:SeekEvent):void { ... } 
 
mediaPlayer.addEventListener(SeekEvent.SEEK_COMPLETED, onSeekCompleted); 
private function onSeekCompleted(event:SeekEvent):void { ... } 
 
...  SeekEvent.SEEK_POSITION_ADJUSTED...  //if the desired 
// seek position is modified by the current advertising policies 
```

