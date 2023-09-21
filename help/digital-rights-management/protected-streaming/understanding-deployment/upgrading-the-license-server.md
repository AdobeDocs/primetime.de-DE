---
title: Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming
description: Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Aktualisieren des Adobe Primetime DRM-Servers für geschütztes Streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Wenn Sie einen Server aktualisieren möchten, auf dem der Primetime-DRM-Server für geschütztes Streaming ausgeführt wird, müssen Sie die Variable `flashaccessserver.war` -Datei, die auf Ihrem Anwendungsserver mit der Datei bereitgestellt wurde, die mit dem neuesten Primetime-DRM bereitgestellt wurde.

Wenn Sie die neuen Konfigurationsoptionen verwenden möchten, müssen Sie die `flashaccess-tenant.xml`. Außerdem müssen Sie [!DNL jsafe.dll] oder [!DNL libjsafe.so] mit der Version, die mit dem neuesten Primetime DRM integriert wurde.
