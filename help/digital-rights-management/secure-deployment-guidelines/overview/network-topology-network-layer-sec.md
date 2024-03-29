---
description: Sicherheitslücken im Netzwerk gehören zu den ersten Bedrohungen für alle Internet- oder Intranet-bezogenen Anwendungsserver. Außerdem müssen Sie Hosts im Netzwerk vor diesen Sicherheitslücken schützen.
title: Sicherheit der Netzwerkschicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Sicherheit der Netzwerkschicht{#network-layer-security}

Sicherheitslücken im Netzwerk gehören zu den ersten Bedrohungen für alle Internet- oder Intranet-bezogenen Anwendungsserver. Außerdem müssen Sie Hosts im Netzwerk vor diesen Sicherheitslücken schützen.

Im Folgenden finden Sie einige gängige Techniken, die Sicherheitslücken im Netzwerk reduzieren:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_djf_lhz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Technik </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Demilitarisierte Zonen (DMZs) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Segmentierung muss auf mindestens zwei Ebenen mit dem Anwendungsserver vorhanden sein, der zum Ausführen von Adobe Primetime DRM verwendet wird, wenn sich Primetime DRM hinter der inneren Firewall befindet. Sie müssen das externe Netzwerk von der DMZ trennen, die die Webserver enthält, und die Webserver müssen vom internen Netzwerk getrennt sein. Sie können Firewalls verwenden, um diese Trennungsebenen zu implementieren. </p> <p>Sie können den Traffic, der durch die einzelnen Netzwerkschichten geleitet wird, kategorisieren und steuern, um sicherzustellen, dass nur das absolute Minimum der erforderlichen Daten zulässig ist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Private IP-Adressen </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie die NAT (Network Address Translation) mit privaten RFC 1918-IP-Adressen auf Primetime-DRM-Anwendungsservern. Sie können private IP-Adressen (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) zuweisen, um es einem Angreifer zu erschweren, Traffic über das Internet zu und von einem internen NAT-Host zu leiten. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Firewalls </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Im Folgenden finden Sie einige Kriterien, die bei der Auswahl einer Firewall-Lösung zu beachten sind: </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">Implementieren Sie Firewalls, die Proxy-Server und/oder statusbehaftete Inspektionen anstelle einfacher Paketfilterlösungen unterstützen. </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">Verwenden Sie eine Firewall, die ein Sicherheitsparadigma unterstützt, in dem Sie alle Dienste mit Ausnahme der explizit zulässigen Dienste ablehnen können. </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">Implementieren Sie eine Firewall-Lösung, die doppelt oder mehrhomogen ist. Diese Architektur bietet ein Höchstmaß an Sicherheit und verhindert, dass nicht autorisierte Benutzer die Firewall-Sicherheit umgehen. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
