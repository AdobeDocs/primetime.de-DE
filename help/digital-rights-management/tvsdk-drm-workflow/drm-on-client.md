---
title: Primetime DRM auf dem Client
description: Primetime DRM auf dem Client
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Primetime DRM auf dem Client{#primetime-drm-on-the-client}

Eine Primetime-TVSDK-Anwendung, die geschützte Inhalte wiedergibt, muss Primetime-DRM-APIs aufrufen, um den Workflow für die Lizenznutzung und die Wiedergabe geschützter Inhalte zu starten. In diesem Workflow erstellt Primetime DRM auf dem Client eine Lizenzanfrage aus den Metadaten der geschützten Inhalte und sendet sie dann an den Primetime DRM-Lizenzserver.

Vor Erteilung der Lizenzanfrage kann der Kunde optional die erforderliche Authentifizierung/Autorisierung durchführen (je nach Ihren Geschäftsregeln).
