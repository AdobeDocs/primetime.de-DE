---
description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.
seo-description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.
seo-title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
uuid: a7b5c9a6-f546-4d3a-9d49-7e5484acff7a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen {#define-fallback-ad-behavior-for-vmap-inline-ads}

Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.

1. Wird `setFallbackOnInvalidCreativeEnabled` `true` so eingestellt, dass VMAP zurückfällt, wenn der Medientyp für eine lineare/Inline-Anzeige für HLS ungültig ist.

   Der Standardwert ist `false`. Wenn eine lineare Anzeige fehlschlägt, weil sie einen ungültigen Medientyp hat oder weil die Anzeige nicht neu verpackt werden kann, erlaubt dieses Flag Primetime und die Entscheidungsfindung dasselbe Ausweichverhalten wie eine leere VAST-Anzeige.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```

