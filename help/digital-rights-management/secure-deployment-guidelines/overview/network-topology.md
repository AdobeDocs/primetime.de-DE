---
title: Netzwerktopologie - Übersicht
description: Netzwerktopologie - Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Übersicht {#network-topology-overview}

Nach der erfolgreichen Bereitstellung von Adobe Primetime DRM müssen Sie die Sicherheit des Primetime-DRM-Produktionsservers wahren.

>[!NOTE]
>
>Primetime DRM wurde früher als Adobe Access, und davor als Flash Access bezeichnet.

Sie können eine *Reverse Proxy* , um sicherzustellen, dass externe und interne Benutzer verschiedene Sätze von URLs für Primetime-DRM-Webanwendungen erhalten. *Reverse Proxy* ist sicherer, als dass Benutzer eine direkte Verbindung zum Anwendungsserver herstellen können, auf dem Primetime DRM ausgeführt wird. Diese Konfiguration führt alle HTTP-Anfragen für den Anwendungsserver durch, auf dem Primetime DRM ausgeführt wird. Benutzer können nur auf den Reverse-Proxy zugreifen und nur die URL-Verbindungen versuchen, die vom Reverse-Proxy unterstützt werden.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)
