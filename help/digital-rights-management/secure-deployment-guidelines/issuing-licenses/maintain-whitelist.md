---
description: Eine Whitelist ist eine Liste vertrauenswürdiger Entitäten.
seo-description: Eine Whitelist ist eine Liste vertrauenswürdiger Entitäten.
seo-title: Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten
title: Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten{#maintain-a-whitelist-of-trusted-content-packagers}

Eine Whitelist ist eine Liste vertrauenswürdiger Entitäten.

Bei Content Packagern handelt es sich bei den Entitäten um Organisationen, denen der Eigentümer des Inhalts vertraut, die Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Primetime DRM sollten Sie eine Whitelist vertrauenswürdiger Inhaltspakete führen. Sie müssen auch die Identität des Content Packager in den DRM-Metadaten einer DRM-geschützten Datei überprüfen, bevor Sie eine Lizenz ausstellen.

Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
