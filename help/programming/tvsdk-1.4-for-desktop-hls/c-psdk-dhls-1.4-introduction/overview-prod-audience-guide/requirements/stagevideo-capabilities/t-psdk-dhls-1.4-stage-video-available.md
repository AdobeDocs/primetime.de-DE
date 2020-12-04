---
description: Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann ermitteln, ob StageVideo verfügbar ist, indem Sie auf das StageVideoAvailabilityEvent warten.
seo-description: Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann ermitteln, ob StageVideo verfügbar ist, indem Sie auf das StageVideoAvailabilityEvent warten.
seo-title: Überprüfen, ob StageVideo verfügbar ist
title: Überprüfen, ob StageVideo verfügbar ist
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---


# Überprüfen, ob StageVideo verfügbar ist{#check-whether-stagevideo-is-available}

Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann ermitteln, ob StageVideo verfügbar ist, indem Sie auf das StageVideoAvailabilityEvent warten.

Ab Flash 15 und höher, wenn die Hardware `StageVideo` nicht verfügbar ist, wird sie auf Software `StageVideo` zurückgesetzt. Für Flash 14 und früher können Sie festlegen, ob `StageVideo` verfügbar ist. Wenn `StageVideo` nicht verfügbar ist, können Sie `StageVideoAvailabilityEvent` verwenden, um zu verstehen, warum es nicht verfügbar ist.

1. Suchen Sie nach `StageVideoAvailabilityEvent`, um festzustellen, ob `StageVideo` verfügbar ist.

   Beispiel:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Wenn `StageVideo` nicht verfügbar ist, überprüfen Sie `flash.media.StageVideoAvailabilityReason`.
