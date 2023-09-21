---
title: Sicherheit der Netzwerkschicht
description: Sicherheit der Netzwerkschicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Sicherheit der Netzwerkschicht{#network-layer-security}

Sicherheitslücken im Netzwerk gehören zu den ersten Bedrohungen für alle Internet- oder Intranet-bezogenen Anwendungsserver. In diesem Abschnitt wird der Prozess beschrieben, wie Hosts im Netzwerk gegen diese Verwundbarkeiten gehärtet werden. Es befasst sich mit der Netzwerksegmentierung, der Stapelhärtung des TCP/IP-Stacks (Transmission Control Protocol/Internet Protocol) und der Verwendung von Firewalls für den Hostschutz.

In dieser Tabelle werden gängige Techniken beschrieben, die Sicherheitslücken im Netzwerk reduzieren.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-djf-lhz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Technik </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Demilitarisierte Zonen (DMZs) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Segmentierung muss in mindestens zwei Ebenen vorhanden sein, wobei sich der Anwendungsserver, der zum Ausführen von Adobe Access verwendet wird, hinter der inneren Firewall befindet. Trennen Sie das externe Netzwerk von der DMZ, die die Webserver enthält, die wiederum vom internen Netzwerk getrennt werden müssen. Verwenden Sie Firewalls, um die Trennungsschichten zu implementieren. Kategorisieren und steuern Sie den Traffic, der durch die einzelnen Netzwerkschichten geleitet wird, um sicherzustellen, dass nur das absolute Minimum der erforderlichen Daten zulässig ist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Private IP-Adressen </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie die NAT (Network Address Translation) mit privaten RFC 1918-IP-Adressen auf Adobe Access-Anwendungsservern. Weisen Sie private IP-Adressen (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) zu, um es einem Angreifer zu erschweren, Traffic über das Internet zu und von einem internen NAT-Host zu leiten. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Firewalls </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie die folgenden Kriterien, um eine Firewall-Lösung auszuwählen: </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">Implementieren Sie Firewalls, die Proxy-Server und/oder stateful-Inspektionen anstelle einfacher Paketfilterlösungen unterstützen. </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">Verwenden Sie eine Firewall, die ein Sicherheitsparadigma unterstützt, in dem Sie alle Dienste mit Ausnahme der explizit zulässigen Dienste ablehnen können. </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">Implementieren Sie eine Firewall-Lösung, die doppelt oder mehrhomogen ist. Diese Architektur bietet ein Höchstmaß an Sicherheit und hilft, zu verhindern, dass nicht autorisierte Benutzer die Firewall-Sicherheit umgehen. </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
