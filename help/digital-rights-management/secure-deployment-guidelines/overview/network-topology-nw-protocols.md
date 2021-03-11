---
description: Wenn Sie eine sichere Netzwerkarchitektur konfigurieren, sind Netzwerkprotokolle für die Interaktion zwischen Adobe Primetime DRM und anderen Systemen in Ihrem Unternehmensnetzwerk erforderlich.
title: Adobe Primetime DRM-Netzwerkprotokolle
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Adobe Primetime DRM-Netzwerkprotokolle {#adobe-primetime-drm-network-protocols}

Wenn Sie eine sichere Netzwerkarchitektur konfigurieren, sind Netzwerkprotokolle für die Interaktion zwischen Adobe Primetime DRM und anderen Systemen in Ihrem Unternehmensnetzwerk erforderlich.

Wenn Sie eine sichere Netzwerkarchitektur konfigurieren, sind für diese Interaktion die folgenden Netzwerkprotokolle erforderlich:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Protokoll </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Verwendung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR®- und Adobe Primetime-Clients kommunizieren mit Primetime DRM über HTTP. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS (optional) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR- und Adobe Primetime-Clients können HTTPS für die Kommunikation mit Primetime DRM verwenden. HTTPS (SSL) ist nur dann erforderlich, wenn Sie FMRMS 1.x-Clients unterstützen. Weitere Informationen finden Sie unter <a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local"> Eingehende URLs </a> und Konfigurieren von SSL. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Anschlüsse für Anwendungsserver {#ports-for-application-servers}

Sie können den Adobe Primetime DRM-Lizenzserver für die Verwendung eines beliebigen Netzwerkports konfigurieren.

Diese Anschlüsse müssen auf der inneren Firewall aktiviert oder deaktiviert werden, je nachdem, welche Netzwerkfunktionalität Sie für Clients zulassen möchten, die eine Verbindung zu dem Anwendungsserver herstellen, auf dem Primetime DRM ausgeführt wird.

## Konfigurieren von SSL {#configuring-ssl}

Der Secure Sockets Layer (SSL) ist nur erforderlich, wenn Sie Flash Media Rights Management Server 1.x-Clients unterstützen müssen.

SSL mit Clientauthentifizierung ist für den Adobe Primetime DRM Key Server erforderlich. Weitere Informationen finden Sie unter [Verwenden des Adobe Primetime DRM-Schlüsselservers](../../using-the-drm-key-server/requirements.md).