---
title: Kritikalität der DRM-Politik
description: Kritikalität der DRM-Politik
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# DRM-Richtlinienkritik{#drm-policy-criticality}

Wenn Sie planen, neue Nutzungsregeln in einer DRM-Richtlinie anzuwenden, und wenn Sie diese DRM-Richtlinie in Inhalten verwenden möchten, die für ältere Lizenzserver gepackt wurden (und daher die neuen Nutzungsregeln nicht korrekt interpretieren), müssen Sie möglicherweise angeben, wie ältere Lizenzserver sich verhalten müssen. Standardmäßig ist die DRM-Richtlinienkritik auf `true` eingestellt.

Diese Einstellung bedeutet, dass der Lizenzserver alle Teile der DRM-Richtlinie verarbeiten muss, bevor eine Lizenz generiert werden kann, die die angegebene DRM-Richtlinie verwendet. Wenn die DRM-Richtlinienkritik auf `false` eingestellt ist, kann ein älterer Lizenzserver die Teile der DRM-Richtlinie ignorieren, die er nicht richtig interpretieren kann. Daher enthalten alle vom Server generierten Lizenzen keine neuen Nutzungsregeln.

Primetime-DRM-Server, die Version 2.0.2 des SDK oder höher unterstützen, akzeptieren die Einstellung für die DRM-Richtlinienkritik.
