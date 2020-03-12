---
seo-title: Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming
title: Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Wenn Sie einen Server aktualisieren möchten, auf dem Primetime DRM Server für geschütztes Streaming ausgeführt wird, müssen Sie die auf Ihrem Anwendungsserver bereitgestellte `flashaccessserver.war` Datei durch die Datei ersetzen, die im neuesten Primetime DRM enthalten ist.

Wenn Sie die neuen Konfigurationsoptionen verwenden möchten, müssen Sie die des Servers aktualisieren `flashaccess-tenant.xml`. Sie müssen auch die Version aktualisieren [!DNL jsafe.dll] oder [!DNL libjsafe.so] mit der die neueste Primetime DRM enthalten ist.
