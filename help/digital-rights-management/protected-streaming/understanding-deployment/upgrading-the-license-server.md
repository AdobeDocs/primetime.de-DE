---
seo-title: Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren
title: Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Wenn Sie einen Server aktualisieren möchten, auf dem Primetime DRM Server für geschütztes Streaming ausgeführt wird, müssen Sie die `flashaccessserver.war`-Datei, die auf Ihrem Anwendungsserver bereitgestellt wurde, durch die Datei ersetzen, die im neuesten Primetime DRM enthalten ist.

Wenn Sie die neuen Konfigurationsoptionen verwenden möchten, müssen Sie die `flashaccess-tenant.xml` Ihres Servers aktualisieren. Sie müssen auch [!DNL jsafe.dll] oder [!DNL libjsafe.so] mit der Version aktualisieren, die in der neuesten Primetime DRM enthalten ist.
