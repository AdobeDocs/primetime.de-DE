---
description: Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann bestimmen, ob StageVideo verfügbar ist, indem sie auf das StageVideoAvailabilityEvent überwacht.
title: Überprüfen, ob StageVideo verfügbar ist
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Überprüfen, ob StageVideo verfügbar ist{#check-whether-stagevideo-is-available}

Wenn StageVideo nicht verfügbar ist und Ihre Anwendung versucht, StageVideo zu verwenden, gibt das TVSDK keinen Fehler aus. Ihre Anwendung kann bestimmen, ob StageVideo verfügbar ist, indem sie auf das StageVideoAvailabilityEvent überwacht.

von Flash 15 und höher, wenn Hardware `StageVideo` nicht verfügbar ist, wird auf Software zurückgesetzt `StageVideo`. Bei Flash 14 und früher können Sie bestimmen, ob `StageVideo` ist verfügbar. Wenn `StageVideo` nicht verfügbar ist, können Sie `StageVideoAvailabilityEvent` um zu verstehen, warum sie nicht verfügbar ist.

1. Suchen Sie nach `StageVideoAvailabilityEvent` um festzustellen, ob `StageVideo` ist verfügbar.

   Beispiel:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Wenn `StageVideo` nicht verfügbar ist, überprüfen Sie `flash.media.StageVideoAvailabilityReason`.
