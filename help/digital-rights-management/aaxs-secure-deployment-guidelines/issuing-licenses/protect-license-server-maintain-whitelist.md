---
seo-title: Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten
title: Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Whitelist von Paketen mit vertrauenswürdigen Inhalten verwalten{#maintain-a-whitelist-of-trusted-content-packagers}

Eine *Whitelist* ist eine Liste vertrauenswürdiger Entitäten. Bei Content Packagern handelt es sich um Organisationen, denen der Eigentümer des Inhalts vertraut, die FLV-/F4V-Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Access wird empfohlen, eine Whitelist vertrauenswürdiger Inhaltspakete zu führen und die Identität des Inhalts-Packager in den DRM-Metadaten (DRM-Header) einer DRM-geschützten Datei zu überprüfen, bevor eine Lizenz erteilt wird.

Weitere Informationen zum Abrufen von Informationen zur Entität, die den Inhalt verpackt hat, finden Sie `V2ContentMetaData.getPackagerInfo()` in der *Adobe Access API-Referenz*.
