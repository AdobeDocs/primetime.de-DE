---
title: Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren
description: Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Adobe Primetime DRM-Server für geschütztes Streaming aktualisieren{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Wenn Sie einen Server aktualisieren möchten, auf dem Primetime DRM Server für geschütztes Streaming ausgeführt wird, müssen Sie die `flashaccessserver.war`-Datei, die auf Ihrem Anwendungsserver bereitgestellt wurde, durch die Datei ersetzen, die im neuesten Primetime DRM enthalten ist.

Wenn Sie die neuen Konfigurationsoptionen verwenden möchten, müssen Sie die `flashaccess-tenant.xml` Ihres Servers aktualisieren. Sie müssen auch [!DNL jsafe.dll] oder [!DNL libjsafe.so] mit der Version aktualisieren, die in der neuesten Primetime DRM enthalten ist.
