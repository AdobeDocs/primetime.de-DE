---
title: Standard-AAXS DRM-Workflow
description: Standard-AAXS DRM-Workflow
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Standard-AAXS-DRM-Workflow{#standard-aaxs-drm-workflow}

1. (Paket) Das AAXS Java SDK generiert einen zufälligen CEK.
1. (Paket) Das CEK wird zum Verschlüsseln von Inhalten verwendet.
1. (Paket) Das CEK wird mit dem öffentlichen Schlüssel des AAXS License Servers verschlüsselt.
1. (Paket) Das verschlüsselte CEK wird in die DRM-Metadaten des Inhalts eingefügt.
1. Das Gerät versucht, Inhalte wiederzugeben, indem es eine Lizenz vom AAXS-Server anfordert.
1. (Lizenzierung) Der AAXS-Server verwendet seinen privaten Schlüssel, um den CEK aus den Metadaten zu entschlüsseln.
1. (Lizenzierung) Der AAXS-Server gibt dem Gerät eine Lizenz aus, die das CEK enthält.
