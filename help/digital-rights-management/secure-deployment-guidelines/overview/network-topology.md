---
seo-title: Übersicht über die Netzwerktopologie
title: Übersicht über die Netzwerktopologie
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Übersicht {#network-topology-overview}

Nach der erfolgreichen Bereitstellung von Adobe Primetime DRM müssen Sie die Sicherheit des Primetime DRM-Produktionsservers gewährleisten.

>[!NOTE]
>
>Primetime DRM war früher als Adobe Access bekannt und davor als Flash Access.

Sie können einen *Reverse-Proxy* verwenden, um sicherzustellen, dass für externe und interne Benutzer verschiedene URLs für Primetime-DRM-Webanwendungen verfügbar sind. *Reverse* proxys ist sicherer, als es Benutzern zu ermöglichen, eine direkte Verbindung mit dem Anwendungsserver herzustellen, auf dem Primetime DRM ausgeführt wird. Diese Konfiguration führt alle HTTP-Anfragen für den Anwendungsserver durch, auf dem Primetime DRM ausgeführt wird. Benutzer können nur auf den Reverse-Proxy zugreifen und nur die URL-Verbindungen versuchen, die vom Reverse-Proxy unterstützt werden.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)