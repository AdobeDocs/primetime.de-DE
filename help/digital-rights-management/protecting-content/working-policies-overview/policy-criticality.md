---
title: Kritische DRM-Politik
description: Kritische DRM-Politik
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Kritische DRM-Politik{#drm-policy-criticality}

Wenn Sie planen, neue Nutzungsregeln in einer DRM-Richtlinie anzuwenden und diese DRM-Richtlinie in Inhalten verwenden möchten, die für ältere Lizenzserver gepackt wurden (und daher die neuen Nutzungsregeln nicht korrekt interpretieren), müssen Sie möglicherweise angeben, wie sich ältere Lizenzserver verhalten müssen. Standardmäßig ist die kritische DRM-Politik auf `true`.

Diese Einstellung gibt an, dass der Lizenzserver alle Teile der DRM-Richtlinie verarbeiten muss, bevor er eine Lizenz generieren kann, die die angegebene DRM-Richtlinie verwendet. Wenn die kritische DRM-Politik auf `false`kann ein älterer Lizenzserver die Teile der DRM-Richtlinie ignorieren, die nicht richtig interpretiert werden können. Daher enthalten alle vom Server generierten Lizenzen keine neuen Nutzungsregeln.

Primetime-DRM-Server, die Version 2.0.2 des SDK oder höher unterstützen, akzeptieren die Einstellung für die kritische DRM-Richtlinie.
