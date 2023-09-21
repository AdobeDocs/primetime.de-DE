---
title: Ausgabeschutzelemente
description: Ausgabeschutzelemente
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Ausgabeschutzelemente {#output-protection-controls}

**Steuern Sie, ob die Ausgabe auf externe Rendering-Geräte geschützt ist. Geben Sie analoge und digitale Ausgaben unabhängig voneinander an.**

Steuert, ob die Ausgabe auf externe Rendering-Geräte beschränkt werden soll. Ein externes Gerät ist definiert als ein Video- oder Audiogerät, das nicht in den Computer eingebettet ist. Die Liste der externen Geräte schließt integrierte Anzeigen aus, z. B. in Notebooks. Analog- und digitale Ausgabebeschränkungen können unabhängig angegeben werden.

Die folgenden Optionen/Durchsetzungsebenen sind verfügbar:

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">In Analoggeräten unterstützt </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">In digitalen Geräten unterstützt </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Erforderlich</b> — Der Ausgabeschutz für Analog Copy Copy Protection (AKP) oder Copy Generation Management System - Analog (CGMS-A) muss aktiviert sein, damit Inhalte auf einem externen Gerät wiedergegeben werden können. Adobe Access-Clients müssen den Ausgabeschutz über AKP oder CGMS-A aktivieren. Auf Geräten, die beide unterstützen, versuchen die Adobe Access 3.0-Clients beide zu aktivieren. Die Wiedergabe des Inhalts darf jedoch nur von einer aktiviert sein. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">AKP erforderlich</b> — Der Schutz der AKP-Produktion ist erforderlich. Die Wiedergabe ist auf CGMS-A nicht zulässig. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Client mit Adobe Access 2.0 so, als ob die Option "Keine Wiedergabe"angegeben wäre. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A erforderlich</b> — CGMS-A-Ausgabeschutz ist erforderlich. Wiedergabe ist in AKP nicht zulässig. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Client mit Adobe Access 2.0 so, als ob die Option "Keine Wiedergabe"angegeben wäre. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Verwendung, falls verfügbar</b> — Versuchen Sie, den Schutz der AKP- und CGMS-A-Ausgabe zu aktivieren, falls verfügbar, und die Wiedergabe zu ermöglichen, falls nicht verfügbar. Adobe Access 3.0-Clients versuchen nach Möglichkeit, sowohl AKP als auch CGMS-A zu aktivieren. Adobe Access 2.0-Clients versuchen nur, AKP oder CGMS-A zu aktivieren. Beispielsweise wird vom Adobe Access-Client versucht, entweder AKP oder CGMS-A zu aktivieren. Wenn der Versuch erfolgreich ist, wird die andere Option nicht aktiviert. Wenn der Versuch fehlschlägt, wird ein zweiter Versuch unternommen, die andere Option zu aktivieren. Selbst wenn beide Versuche fehlschlagen, wird der Inhalt trotzdem wiedergegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">AKP verwenden, falls verfügbar</b> — Versuchen Sie, den Schutz der AKP-Ausgabe zu aktivieren, sofern verfügbar, aber die Wiedergabe zu ermöglichen, falls nicht verfügbar. Der Schutz ist bei CGMS-A nicht verfügbar. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Client mit Adobe Access 2.0 so, als ob die Option "Kein Schutz"angegeben wäre. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Verwenden Sie CGMS-A , falls verfügbar </b>— Versuchen Sie, den CGMS-A-Ausgabeschutz zu aktivieren, falls verfügbar, aber die Wiedergabe zu ermöglichen, wenn nicht verfügbar. Der Schutz der AKP-Staaten ist nicht möglich. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Client mit Adobe Access 2.0 so, als ob die Option "Kein Schutz"angegeben wäre. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Kein Schutz</b> — Für analoge und digitale Ausgaben wird keine Aktivierung zum Schutz der Ausgabe erzwungen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Keine Wiedergabe</b> —Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben nicht zulassen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren. Auf anderen Plattformen (wie Macintosh und Linux) stehen keine unterstützenden Betriebssystemfunktionen für Anwendungen von Drittanbietern zur Verfügung.

Anwendungsbeispiel: Manche Inhalte können Ausgabeschutzkontrollen durchsetzen und das Schutzniveau kann vom Inhaltsdistributor festgelegt werden. Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe auf einem Macintosh versucht wird, gibt der Client keine Inhalte auf externen Geräten wieder. Der Inhalt wird jedoch auf internen Monitoren wiedergegeben.

Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe unter Linux versucht wird, gibt der Client keine Inhalte auf Geräten wieder, da es nicht möglich ist, zwischen internen und externen Geräten zu unterscheiden.

Wenn Sie &quot;Wenn verfügbar verwenden&quot;angeben, wird der Ausgabeschutz nach Möglichkeit aktiviert. Auf Windows-Computern, die das Certified Output Protection Protocol (COPP) unterstützen, wird der Inhalt beispielsweise mit Ausgabeschutz an eine externe Anzeige übergeben. Dieses Beispiel wird manchmal als &quot;auswählbare Ausgabesteuerung&quot;bezeichnet.
