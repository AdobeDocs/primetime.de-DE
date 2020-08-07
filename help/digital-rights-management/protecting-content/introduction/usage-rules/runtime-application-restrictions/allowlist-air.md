---
description: 'null'
seo-description: 'null'
seo-title: Allow list for Primetime DRM applications allowed to play protected content
title: Allow list for Primetime DRM applications allowed to play protected content
uuid: 23dd4faf-7992-4ee9-97ce-c6004ee995c2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Zulassungsliste für Primetime-DRM-Anwendungen zur Wiedergabe geschützter Inhalte {#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

Eine Zulassungsliste gibt die AIR-, iOS- und Android-Anwendungen an, die Inhalte abspielen dürfen. It also specifies AIR and iOS application IDs, minimum version, maximum version, and publisher ID.

Verwendungsbeispiel: Mit dieser Regel können Sie die Wiedergabe auf eine bestimmte Anwendung beschränken oder die Version der Anwendung steuern, die auf Inhalte zugreifen kann.

>[!NOTE]
>
>Wenn Sie Adobe Flash Builder zum Erstellen geschützter Anwendungen verwenden, müssen Sie sicherstellen, dass Sie die Anwendung nicht im Debug-Modus bereitstellen. Wenn Sie eine Anwendung im Debug-Modus bereitstellen, wird der Flash Builder `.debug` an die AIR-Anwendungs-ID angehängt, wodurch sich die Zulassungsliste in Primetime DRM unerwartet verhält.
