---
seo-title: Primetime-DRM auf dem Client
title: Primetime-DRM auf dem Client
uuid: 472180ad-6596-4a24-aa51-7909a75a5e10
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Primetime-DRM auf dem Client{#primetime-drm-on-the-client}

Eine Primetime-TVSDK-Anwendung, die geschützten Inhalt wiedergibt, muss zuerst Primetime-DRM-APIs aufrufen, um den Workflow für den Lizenzkonsum und die Wiedergabe geschützter Inhalte zu starten. In diesem Arbeitsablauf erstellt Primetime DRM auf dem Client eine Lizenzanforderung aus den Metadaten des geschützten Inhalts und sendet diese dann an den Primetime DRM-Lizenzserver.

Vor Erteilung der Lizenzanforderung kann der Kunde optional die erforderliche Authentifizierung/Autorisierung durchführen (je nach Ihren Geschäftsregeln).
