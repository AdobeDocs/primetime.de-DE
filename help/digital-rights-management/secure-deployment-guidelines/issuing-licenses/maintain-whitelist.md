---
description: Eine zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.
seo-description: Eine zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.
seo-title: zulassungsliste von Paketen mit vertrauenswürdigen Inhalten verwalten
title: zulassungsliste von Paketen mit vertrauenswürdigen Inhalten verwalten
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---


# Verwalten einer zulassungsliste vertrauenswürdiger Inhaltspakete{#maintain-a-allowlist-of-trusted-content-packagers}

Eine zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.

Bei Content Packagern handelt es sich bei den Entitäten um Organisationen, denen der Eigentümer des Inhalts vertraut, die Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Primetime DRM sollten Sie eine zulassungsliste von Paketen mit vertrauenswürdigen Inhalten führen. Sie müssen auch die Identität des Content Packager in den DRM-Metadaten einer DRM-geschützten Datei überprüfen, bevor Sie eine Lizenz ausstellen.

Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
