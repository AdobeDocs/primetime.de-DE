---
description: Der Adobe Primetime DRM-Server für geschütztes Streaming ist eine Lizenzserverimplementierung, die auf dem Primetime DRM SDK basiert. Dieser Server stellt Lizenzen für geschützte Inhalte für Primetime DRM-Clients aus.
title: Über den Adobe Primetime DRM-Server für geschütztes Streaming
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Über den Adobe Primetime DRM-Server für geschütztes Streaming{#about-adobe-primetime-drm-server-for-protected-streaming}

Der Adobe Primetime DRM-Server für geschütztes Streaming ist eine Lizenzserverimplementierung, die auf dem Primetime DRM SDK basiert. Dieser Server stellt Lizenzen für geschützte Inhalte für Primetime DRM-Clients aus.

Der Primetime-DRM-Server für geschütztes Streaming unterstützt mehrere Mandanten. Sie können einen einzelnen Server im Auftrag mehrerer Inhaltsverlage hosten, von denen jeder über eigene Konfigurationseinstellungen verfügt. Darüber hinaus unterstützt der Server benutzerdefinierte Autorisierungskomponenten, sodass Sie benutzerdefinierte Logik ausführen können, bevor eine Lizenz erteilt wird.

Dieser Server ist für die Verwendung mit HTTP-Streaming vorgesehen. Daher unterstützt diese Serverimplementierung nicht alle in Primetime DRM verfügbaren Funktionen. Beispielsweise werden keine Benutzerauthentifizierungsanfragen, mehrere Richtlinien, domänengebundene Lizenzen, Lizenzketten oder Synchronisierungsmeldungen unterstützt.

>[!NOTE]
>
>Adobe Primetime DRM hieß früher Adobe Access und davor Flash Access.
