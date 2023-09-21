---
title: Zulassungsliste vertrauenswürdiger Inhaltspakete verwalten
description: Zulassungsliste vertrauenswürdiger Inhaltspakete verwalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Zulassungsliste vertrauenswürdiger Inhaltspakete verwalten {#maintain-a-allowlist-of-trusted-content-packagers}

Ein **Zulassungsliste** ist eine Liste vertrauenswürdiger Entitäten. Bei Inhaltspaketen handelt es sich um Organisationen, denen der Inhaltseigentümer vertraut, um die FLV/F4V-Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Access wird empfohlen, eine Zulassungsliste vertrauenswürdiger Inhaltspakete zu verwalten und die Identität des Inhaltspakets zu überprüfen, der in den DRM-Metadaten (DRM-Header) einer DRM-geschützten Datei enthalten ist, bevor Sie eine Lizenz ausstellen.

Weitere Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter `V2ContentMetaData.getPackagerInfo()` im *Adobe Access API-Referenz*.
