---
description: Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann ermitteln, ob StageVideo verfügbar ist, indem Sie auf das StageVideoAvailabilityEvent warten.
title: Überprüfen, ob StageVideo verfügbar ist
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '124'
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
