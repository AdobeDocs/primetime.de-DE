---
description: Eine Zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.
title: Zulassungsliste von Paketen mit vertrauenswürdigen Inhalten verwalten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Eine Zulassungsliste vertrauenswürdiger Inhaltspakete {#maintain-a-allowlist-of-trusted-content-packagers} verwalten

Eine Zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.

Bei Content Packagern handelt es sich bei den Entitäten um Organisationen, denen der Eigentümer des Inhalts vertraut, die Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Primetime DRM sollten Sie eine Zulassungsliste von Paketen mit vertrauenswürdigen Inhalten verwalten. Sie müssen auch die Identität des Content Packager in den DRM-Metadaten einer DRM-geschützten Datei überprüfen, bevor Sie eine Lizenz ausstellen.

Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
