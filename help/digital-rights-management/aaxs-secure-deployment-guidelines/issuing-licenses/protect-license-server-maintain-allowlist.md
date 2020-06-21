---
seo-title: Verwalten einer zulassungsliste vertrauenswürdiger Inhaltspakete
title: Verwalten einer zulassungsliste vertrauenswürdiger Inhaltspakete
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Verwalten einer zulassungsliste vertrauenswürdiger Inhaltspakete{#maintain-a-allowlist-of-trusted-content-packagers}

Ein *zulassungsliste* ist eine Liste vertrauenswürdiger Entitäten. Bei Content Packagern handelt es sich um Organisationen, denen der Eigentümer des Inhalts vertraut, die FLV-/F4V-Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Access wird empfohlen, eine zulassungsliste der Packager für vertrauenswürdige Inhalte zu verwalten und die Identität des Inhalts-Packagers in den DRM-Metadaten (DRM-Header) einer DRM-geschützten Datei zu überprüfen, bevor eine Lizenz erteilt wird.

Weitere Informationen zum Abrufen von Informationen zur Entität, die den Inhalt verpackt hat, finden Sie `V2ContentMetaData.getPackagerInfo()` in der *Adobe Access API-Referenz*.
