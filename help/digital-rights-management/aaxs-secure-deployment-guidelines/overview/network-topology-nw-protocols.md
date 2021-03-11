---
title: Netzwerkprotokolle, die von Adobe Access verwendet werden
description: Netzwerkprotokolle, die von Adobe Access verwendet werden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Von Adobe Access verwendete Netzwerkprotokolle {#network-protocols-used-by-adobe-access}

Wenn Sie eine sichere Netzwerkarchitektur konfigurieren, sind die in der folgenden Tabelle aufgeführten Netzwerkprotokolle für die Interaktion zwischen Adobe Access und anderen Systemen in Ihrem Unternehmensnetzwerk erforderlich.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-itc-33z-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Protokoll </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Verwendung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR®- und Adobe Primetime-Clients kommunizieren mit Adobe Access über HTTP. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS (optional) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR- und Adobe Primetime-Clients können HTTPS für die Kommunikation mit Adobe Access verwenden. HTTPS (SSL) ist jedoch nicht erforderlich, es sei denn, Sie benötigen Unterstützung für FMRMS 1.x-Clients. Siehe die Hinweise in den Tabellen <a href="network-topology-firewall-rules.md" format="dita" scope="local"> Eingehende URLs</a> und <a href="network-topology-nw-protocols.md"> Konfigurieren von SSL</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>