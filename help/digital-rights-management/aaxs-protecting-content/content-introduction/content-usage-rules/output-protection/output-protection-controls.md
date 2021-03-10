---
title: Ausgabenschutzkontrollen
description: Ausgabenschutzkontrollen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Ausgabenschutzsteuerelemente {#output-protection-controls}

**Steuert, ob die Ausgabe auf externen Renderinggeräten geschützt ist. Geben Sie analoge und digitale Ausgänge unabhängig an.**

Steuert, ob die Ausgabe auf externe Renderinggeräte eingeschränkt werden soll. Ein externes Gerät ist definiert als ein Video- oder Audiogerät, das nicht in den Computer eingebettet ist. Die Liste externer Geräte schließt integrierte Displays wie z. B. in Notebooks aus. Analoge und digitale Ausgabebeschränkungen können unabhängig angegeben werden.

Die folgenden Optionen/Ebenen der Durchsetzung stehen zur Verfügung:

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
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Erforderlich</b> — Der Ausgabeschutz für Analog Copy Copy Protection (AKP) oder Copy Generation Management System - Analog (CGMS-A) muss aktiviert sein, damit Inhalte auf einem externen Gerät wiedergegeben werden können. Adobe Access Clients müssen Ausgabeschutz mit AKP oder CGMS-A aktivieren. Auf Geräten, die beide unterstützen, versuchen die Adobe Access 3.0-Clients, beides zu aktivieren. Für die Wiedergabe des Inhalts muss jedoch nur einer aktiviert sein. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">AKP erforderlich</b> — Der Schutz der AKP-Produktion ist erforderlich. Die Wiedergabe ist auf CGMS-A nicht zulässig. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als ob die Option "Keine Wiedergabe"angegeben wurde. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A erforderlich</b> — CGMS-A-Ausgabeschutz ist erforderlich. Die Wiedergabe auf den AKP-Staaten ist nicht zulässig. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als ob die Option "Keine Wiedergabe"angegeben wurde. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gegebenenfalls</b>  verwenden— Versuchen Sie, den Schutz der AKP- und CGMS-A-Ausgabe zu aktivieren, falls verfügbar, und lassen Sie die Wiedergabe zu, falls nicht verfügbar. Adobe Access 3.0-Clients versuchen, nach Möglichkeit sowohl AKP als auch CGMS-A zu aktivieren. Adobe Access 2.0-Clients versuchen nur, AKP oder CGMS-A zu aktivieren. So wird beispielsweise vom Adobe Access-Client versucht, entweder AKP oder CGMS-A zu aktivieren. Wenn der Versuch erfolgreich ist, wird die andere Option nicht aktiviert. Wenn der Versuch fehlschlägt, wird ein zweiter Versuch unternommen, die andere Option zu aktivieren. Auch wenn beide Versuche fehlschlagen, wird der Inhalt trotzdem wiedergegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">AKP verwenden, falls verfügbar</b> — Versuchen Sie, den Schutz der AKP-Ausgabe zu aktivieren, wenn diese verfügbar ist, aber die Wiedergabe zu ermöglichen, wenn nicht verfügbar. Der Schutz ist auf CGMS-A nicht verfügbar. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als wäre die Option "Kein Schutz"angegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Verwenden Sie CGMS-A, falls verfügbar  </b>— Versuchen Sie, den Schutz der CGMS-A-Ausgabe zu aktivieren, wenn dieser verfügbar ist, lassen Sie die Wiedergabe jedoch zu, falls nicht verfügbar. Für AKP-Staaten ist kein Schutz verfügbar. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als wäre die Option "Kein Schutz"angegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Kein Schutz</b> — Für analoge und digitale Ausgaben wird keine Ausgabeschutzaktivierung erzwungen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Keine Wiedergabe</b>  - Die Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben ist nicht zulässig. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren. Auf anderen Plattformen (wie Macintosh und Linux) stehen keine unterstützenden Betriebssystemfunktionen für Anwendungen von Drittanbietern zur Verfügung.

Verwendungsbeispiel: Einige Inhalte können Ausgabeschutzkontrollen durchsetzen und der Grad des Schutzes kann vom Content-Distributor festgelegt werden. Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe auf einem Macintosh versucht wird, gibt der Client keine Inhalte auf externen Geräten wieder. Der Inhalt wird jedoch auf internen Monitoren wiedergegeben.

Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe unter Linux versucht wird, gibt der Client keine Inhalte auf Geräten wieder, da es nicht möglich ist, zwischen internen und externen Geräten zu unterscheiden.

Wenn Sie &quot;Falls verfügbar verwenden&quot;angeben, wird der Ausgabeschutz nach Möglichkeit aktiviert. Beispielsweise wird der Inhalt auf Windows-Computern, die das zertifizierte Output Protection Protocol (COPP) unterstützen, mit Ausgabeschutz an eine externe Anzeige übergeben. Dieses Beispiel wird manchmal auch als &quot;auswählbare Ausgabesteuerung&quot;bezeichnet.
