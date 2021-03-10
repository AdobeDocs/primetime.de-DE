---
description: Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.
title: Benachrichtigungscodes
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Benachrichtigungscodes {#notification-codes}

Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.

Benachrichtigungsobjekte liefern Informationen zum Status des Players. TVSDK bietet eine chronologisch sortierte Liste von Benachrichtigungsobjekten. Jede Benachrichtigung enthält die folgenden Metadaten:

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Element</b></th> 
   <th colname="2" class="entry"><b> Beschreibung</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> <p>Der Benachrichtigungstyp. </p> <p>Abhängig von der Plattform ist diese Eigenschaft ein aufgezählter Typ mit möglichen Werten für INFO, WARN und ERROR. Dies ist die Gruppierung auf oberster Ebene für Benachrichtigungen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> code</span> </td> 
   <td colname="2"> <p>Die folgenden numerischen Darstellungen werden den Benachrichtigungen zugeordnet: 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">Ereignisse zur Fehlermeldung von 100000 bis 19999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">Ereignis für die Meldung von Warnmeldungen von 20000 bis 29999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">Ereignis für die Information von 300000 bis 399999 </li> 
     </ul> </p> <p>Jeder Bereich auf der obersten Ebene, z. B. Fehler, wird in Unterbereiche unterteilt, wie z. B. 101000 bis 101999, die Wiedergabefehler darstellen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Eine Zeichenfolge, die eine für Menschen lesbare Beschreibung des Benachrichtigungs-Ereignisses enthält, z. B. <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2"> <p>Schlüssel/Wert-Paare, die zusätzliche relevante Informationen zur Benachrichtigung enthalten. </p> <p>Beispielsweise würde ein Schlüssel mit dem Namen <span class="codeph"> URL</span> einen Wert bereitstellen, der eine URL im Zusammenhang mit der Benachrichtigung ist, z. B. eine ungültige URL, die einen Fehler verursacht hat. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Ein Verweis auf ein anderes <span class="codeph">-MediaPlayerNotification</span>-Objekt, das diese Benachrichtigung direkt beeinflusste. </p> <p>Ein Beispiel könnte eine Benachrichtigung über einen Fehler beim Einfügen von Anzeigen sein, der direkt einem Einfügekonflikt in der Zeitleiste entspricht. Nicht alle Benachrichtigungen bieten eine interne Benachrichtigung. </p> </td> 
  </tr> 
 </tbody> 
</table>