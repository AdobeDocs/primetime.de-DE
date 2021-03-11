---
title: Primetime-DRM auf dem Client
description: Primetime-DRM auf dem Client
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Primetime-DRM auf dem Client{#primetime-drm-on-the-client}

Eine Primetime-TVSDK-Anwendung, die geschützten Inhalt wiedergibt, muss zuerst Primetime-DRM-APIs aufrufen, um den Workflow für den Lizenzkonsum und die Wiedergabe geschützter Inhalte zu starten. In diesem Arbeitsablauf erstellt Primetime DRM auf dem Client eine Lizenzanforderung aus den Metadaten des geschützten Inhalts und sendet diese dann an den Primetime DRM-Lizenzserver.

Vor Erteilung der Lizenzanforderung kann der Kunde optional die erforderliche Authentifizierung/Autorisierung durchführen (je nach Ihren Geschäftsregeln).
