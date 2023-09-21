---
description: Das TVSDK-Benachrichtigungssystem erzeugt verschiedene Fehler-, Warnungs- und Informationshinweise, die diagnostische Metadaten bereitstellen.
title: Benachrichtigungscodes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Benachrichtigungscodes {#notification-codes}

Das TVSDK-Benachrichtigungssystem erzeugt verschiedene Fehler-, Warnungs- und Informationshinweise, die diagnostische Metadaten bereitstellen.

Benachrichtigungsobjekte liefern Informationen, die sich auf den Status des Players beziehen. TVSDK bietet eine chronologisch sortierte Liste von Benachrichtigungsobjekten. Jede Benachrichtigung enthält die folgenden Metadaten:

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
   <td colname="2"> <p>Der Benachrichtigungstyp. </p> <p>Abhängig von der Plattform ist diese Eigenschaft ein Auflistungstyp mit möglichen Werten für INFO, WARN und ERROR. Dies ist die Gruppierung der obersten Ebene für Benachrichtigungen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> code</span> </td> 
   <td colname="2"> <p>Den Benachrichtigungen werden die folgenden numerischen Darstellungen zugewiesen: 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">Fehlerbenachrichtigungsereignisse von 100000 bis 199999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">Warnungen bei Benachrichtigungen von 20000 bis 29999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">Ereignisse bei Informationsmeldungen von 300000 bis 399999 </li> 
     </ul> </p> <p>Jeder Bereich der obersten Ebene, wie z. B. Fehler, ist in Unterbereiche unterteilt, z. B. 101000 bis 101999, die Wiedergabefehler darstellen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Eine Zeichenfolge, die eine für Menschen lesbare Beschreibung des Benachrichtigungsereignisses enthält, z. B. <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> Metadaten</span> </td> 
   <td colname="2"> <p>Schlüssel-Wert-Paare, die zusätzliche relevante Informationen zur Benachrichtigung enthalten. </p> <p>Beispiel: ein Schlüssel mit dem Namen <span class="codeph"> URL</span> einen Wert bereitstellen, der eine mit der Benachrichtigung verknüpfte URL ist, z. B. eine ungültige URL, die einen Fehler verursacht hat. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Ein Verweis auf eine andere <span class="codeph"> MediaPlayerNotification</span> -Objekt, das diese Benachrichtigung direkt beeinflusst hat. </p> <p>Ein Beispiel ist eine Benachrichtigung über einen Fehler beim Einfügen von Anzeigen, der direkt einem Einfügekonflikt zwischen Zeitlinien entspricht. Nicht alle Benachrichtigungen enthalten eine innere Benachrichtigung. </p> </td> 
  </tr> 
 </tbody> 
</table>
