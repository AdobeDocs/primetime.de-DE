---
title: Standard-DRM-Workflow "AAXS"
description: Standard-DRM-Workflow "AAXS"
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Standard-DRM-Workflow &quot;AAXS&quot;{#standard-aaxs-drm-workflow}

1. (Package) Das AXS Java SDK generiert einen zufälligen CEK.
1. (Package) Das CEK wird zum Verschlüsseln von Inhalten verwendet.
1. (Package) Das CEK wird mithilfe des öffentlichen Schlüssels von AAXS License Server verschlüsselt.
1. (Package) Das verschlüsselte CEK wird in die DRM-Metadaten des Inhalts eingefügt.
1. Das Gerät versucht, Inhalte wiederzugeben, indem es eine Lizenz vom AXS-Server anfordert.
1. (Lizenzierung) Der AXS-Server verwendet seinen privaten Schlüssel zum Entschlüsseln des CEK aus den Metadaten.
1. (Lizenzierung) Der AXS-Server gibt dem Gerät eine Lizenz aus, die das CEK enthält.
