---
seo-title: Sicherheit der Netzwerkschicht
title: Sicherheit der Netzwerkschicht
uuid: bd53bccf-1130-4189-97ec-4259bd25762f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Sicherheit der Netzwerkschicht{#network-layer-security}

Sicherheitslücken im Netzwerk gehören zu den ersten Bedrohungen für jeden Internet- oder Intranet-orientierten Anwendungsserver. In diesem Abschnitt wird der Prozess zum Härten von Hosts im Netzwerk gegen diese Verwundbarkeiten beschrieben. Es befasst sich mit der Segmentierung des Netzwerks, der Stack-Härtung des Transmission Control Protocol/Internet Protocol (TCP/IP) und der Verwendung von Firewalls zum Schutz des Hosts.

In dieser Tabelle werden gängige Techniken beschrieben, mit denen Sicherheitslücken im Netzwerk verringert werden.

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Die Segmentierung muss in mindestens zwei Ebenen bestehen, wobei sich der Anwendungsserver, der zum Ausführen von Adobe Access verwendet wird, hinter der inneren Firewall befindet. Trennen Sie das externe Netzwerk von der DMZ, die die Webserver enthält, die wiederum vom internen Netzwerk getrennt werden müssen. Verwenden Sie Firewalls, um die Ebenen der Trennung zu implementieren. Kategorisieren und steuern Sie den Traffic, der durch die einzelnen Netzwerkebenen verläuft, um sicherzustellen, dass nur das absolute Minimum der erforderlichen Daten zulässig ist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Private IP-Adressen </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie NAT (Network Address Translation) mit RFC 1918 privaten IP-Adressen auf Anwendungsservern von Adobe Access. Weisen Sie private IP-Adressen (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) zu, um es einem Angreifer zu erschweren, Traffic über das Internet zu und von einem internen NAT-Host zu leiten. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Firewalls </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verwenden Sie die folgenden Kriterien, um eine Firewall-Lösung auszuwählen: </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">Implementieren Sie Firewalls, die Proxyserver und/oder stateful Inspection anstelle einfacher Paketfilterlösungen unterstützen. </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">Verwenden Sie eine Firewall, die ein Sicherheitsparadigma unterstützt, bei dem Sie alle Dienste mit Ausnahme der explizit zulässigen Dienste ablehnen können. </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">Implementieren Sie eine Firewall-Lösung mit zwei- oder mehrheimischen Elementen. Diese Architektur bietet die größte Sicherheit und hilft, nicht autorisierte Benutzer daran zu hindern, die Firewall-Sicherheit zu umgehen. </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

