---
description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.
title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen {#define-fallback-ad-behavior-for-vmap-inline-ads}

Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.

1. Setzen Sie `setFallbackOnInvalidCreativeEnabled` auf `true`, damit VMAP zurückfällt, wenn der Medientyp für eine lineare/inline-Anzeige für HLS ungültig ist.

   Der Standardwert ist `false`. Wenn eine lineare Anzeige fehlschlägt, weil sie einen ungültigen Medientyp hat oder weil die Anzeige nicht neu verpackt werden kann, erlaubt dieses Flag Primetime und die Entscheidungsfindung dasselbe Ausweichverhalten wie eine leere VAST-Anzeige.

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```

