---
seo-title: Ausgabenschutzkontrollen
title: Ausgabenschutzkontrollen
uuid: 1f4cc617-7f14-4952-8e61-6acbdf01d10e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Ausgabenschutzkontrollen {#output-protection-controls}

**Steuert, ob die Ausgabe auf externen Renderinggeräten geschützt ist. Geben Sie analoge und digitale Ausgänge unabhängig voneinander an.**

Steuert, ob die Ausgabe auf externe Renderinggeräte eingeschränkt werden soll. Ein externes Gerät ist definiert als ein Video- oder Audiogerät, das nicht in den Computer eingebettet ist. The list of external devices excludes integrated displays, such as in notebook computers. Analog and digital output restrictions can be specified independently.

The following options/levels of enforcement are available:

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Supported in analog devices </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">Supported in digital devices </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Required</b> — Analog Copy Protection (ACP) or Copy Generation Management System - Analog (CGMS-A) output protection must be enabled in order to play content to an external device. Adobe Access clients must enable output protection using ACP or CGMS-A. On devices that support both, the Adobe Access 3.0 clients will attempt to enable both. However, only one must be enabled to play the content. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">YES </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">YES </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP Required</b> — ACP output protection is required. Playback is not allowed on CGMS-A. Adobe Access 2.0 clients do not support this option. If set, an Adobe Access 2.0 client will behave as if the “No Playback” option was specified. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A erforderlich</b> — CGMS-A-Ausgabeschutz ist erforderlich. Die Wiedergabe auf den AKP-Staaten ist nicht zulässig. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als ob die Option "Keine Wiedergabe"angegeben wurde. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Gegebenenfalls</b> verwenden — Versuchen Sie, den Schutz der AKP- und CGMS-A-Ausgabe zu aktivieren, falls verfügbar, und lassen Sie die Wiedergabe zu, falls nicht verfügbar. Adobe Access 3.0-Clients versuchen, nach Möglichkeit sowohl AKP als auch CGMS-A zu aktivieren. Adobe Access 2.0-Clients versuchen nur, AKP oder CGMS-A zu aktivieren. So wird beispielsweise vom Adobe Access-Client versucht, entweder AKP oder CGMS-A zu aktivieren. Wenn der Versuch erfolgreich ist, wird die andere Option nicht aktiviert. Wenn der Versuch fehlschlägt, wird ein zweiter Versuch unternommen, die andere Option zu aktivieren. Auch wenn beide Versuche fehlschlagen, wird der Inhalt trotzdem wiedergegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">AKP verwenden, falls verfügbar</b> — Versuchen Sie, den Schutz der AKP-Ausgabe zu aktivieren, wenn diese verfügbar ist, aber die Wiedergabe zu ermöglichen, wenn nicht verfügbar. Der Schutz ist auf CGMS-A nicht verfügbar. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als wäre die Option "Kein Schutz"angegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Verwenden Sie CGMS-A, falls verfügbar </b>— Versuchen Sie, den Schutz der CGMS-A-Ausgabe zu aktivieren, wenn dieser verfügbar ist, lassen Sie die Wiedergabe jedoch zu, falls nicht verfügbar. Für AKP-Staaten ist kein Schutz verfügbar. Adobe Access 2.0-Clients unterstützen diese Option nicht. Wenn diese Option aktiviert ist, verhält sich ein Client für Adobe Access 2.0 so, als wäre die Option "Kein Schutz"angegeben. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Kein Schutz</b> — Für analoge und digitale Ausgaben wird keine Ausgabeschutzaktivierung erzwungen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">YES </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Keine Wiedergabe</b> - Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben nicht zulassen. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">JA </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren. Auf anderen Plattformen (wie Macintosh und Linux) stehen keine unterstützenden Betriebssystemfunktionen für Anwendungen von Drittanbietern zur Verfügung.

Example use case: Some content might enforce output protection controls, and the level of protection can be set by the content distributor. If “Required” is specified and playback is attempted on a Macintosh, the client does not play back content on external devices. The content will, however, play back on internal monitors.

If “Required” is specified and playback is attempted on Linux, the client does not play back content on any devices because it is not possible to differentiate between internal and external devices.

If you specify “Use if available”, output protection is turned on where possible. For example, on Windows machines that support the Certified Output Protection Protocol (COPP), the content is passed with output protection to an external display. This example is sometimes known as “selectable output control”.
