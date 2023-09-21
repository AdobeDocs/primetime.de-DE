---
description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine Inline-VMAP-Anzeige einen ungültigen Medientyp enthält.
title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen {#define-fallback-ad-behavior-for-vmap-inline-ads}

Sie können die Ausweichmöglichkeit aktivieren, wenn eine Inline-VMAP-Anzeige einen ungültigen Medientyp enthält.

1. Satz `setFallbackOnInvalidCreativeEnabled` nach `true` , damit VMAP zurückfällt, wenn der Medientyp für eine lineare/Inline-Anzeige für HLS ungültig ist.

   Der Standardwert ist `false`. Wenn eine lineare Anzeige fehlschlägt, weil sie einen ungültigen Medientyp aufweist oder weil die Anzeige nicht neu verpackt werden kann, ermöglicht dieses Flag, dass die Primetime-Anzeigenentscheidung dasselbe Ausweichverhalten wie ein leerer VAST-Wrapper anwendet.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
