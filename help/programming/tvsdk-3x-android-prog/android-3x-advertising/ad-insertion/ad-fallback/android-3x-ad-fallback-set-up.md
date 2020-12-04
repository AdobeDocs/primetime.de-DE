---
description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.
seo-description: Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.
seo-title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
title: Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen
uuid: bc8cb0b4-5ea9-429b-ab5d-746c6f03e74b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '130'
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
