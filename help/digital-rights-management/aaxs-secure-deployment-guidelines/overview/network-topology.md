---
title: Netzwerktopologie - Übersicht
description: Netzwerktopologie - Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# Netzwerktopologie - Übersicht {#network-topology-overview}

Nachdem Sie Adobe Access erfolgreich bereitgestellt haben, ist es wichtig, die Sicherheit Ihrer Umgebung zu gewährleisten. In diesem Abschnitt werden die Aufgaben beschrieben, die zur Gewährleistung der Sicherheit Ihres Adobe Access-Produktionsservers erforderlich sind.

Verwenden Sie eine *Reverse Proxy* , um sicherzustellen, dass sowohl externe als auch interne Benutzer verschiedene Sätze von URLs für Adobe Access-Webanwendungen erhalten. Diese Konfiguration ist sicherer, als dass Benutzer direkt eine Verbindung zum Anwendungsserver herstellen können, auf dem Adobe Access ausgeführt wird. Der Reverse-Proxy führt alle HTTP-Anfragen für den Anwendungsserver aus, der Adobe Access ausführt. Benutzer haben nur Netzwerkzugriff auf den Reverse-Proxy und können nur die URL-Verbindungen versuchen, die vom Reverse-Proxy unterstützt werden.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)
