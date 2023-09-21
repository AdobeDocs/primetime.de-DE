---
description: Das TVSDK-Benachrichtigungssystem erzeugt verschiedene Fehler-, Warnungs- und Informationshinweise, die diagnostische Metadaten bereitstellen.
title: TVSDK-Benachrichtigungssystem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# TVSDK-Benachrichtigungssystem {#tvsdk-notification-system}

Das TVSDK-Benachrichtigungssystem erzeugt verschiedene Fehler-, Warnungs- und Informationshinweise, die diagnostische Metadaten bereitstellen.

Benachrichtigungsobjekte liefern Informationen zum Status des Players. TVSDK bietet eine chronologisch sortierte Liste von Benachrichtigungsobjekten. Jede Benachrichtigung enthält die folgenden Metadaten:

<table frame="all" colsep="1" rowsep="1" id="table_DBA8CACF02DB4AF2B053E560850B49CE"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Element </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> Der Benachrichtigungstyp. Abhängig von der Plattform bezieht sich diese Eigenschaft auf einen Auflistungstyp mit möglichen Werten für INFO, WARN oder ERROR. Dies ist die Gruppierung der obersten Ebene für Benachrichtigungen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span> </td> 
   <td colname="2">Die der Benachrichtigung zugewiesene numerische Darstellung. 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">Fehlerbenachrichtigungsereignisse von 100000 bis 199999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">Warnungen bei Benachrichtigungen von 20000 bis 29999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">Ereignisse bei Informationsmeldungen von 300000 bis 399999 </li> 
    </ul> <p>Jeder Bereich der obersten Ebene, wie z. B. Fehler, ist in Unterbereiche unterteilt, z. B. 101000 bis 101999, die Wiedergabefehler darstellen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Eine Zeichenfolge, die eine für Menschen lesbare Beschreibung des Codes enthält, z. B. <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> Metadaten</span> </td> 
   <td colname="2">Schlüssel-Wert-Paare, die zusätzliche relevante Informationen zur Benachrichtigung enthalten. Beispiel: ein Schlüssel mit dem Namen <span class="codeph"> URL</span> mit einem Wert gepaart werden, der eine mit der Benachrichtigung verknüpfte URL ist, z. B. eine ungültige URL, die einen Fehler verursacht hat. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2">Ein Verweis auf eine andere <span class="codeph"> PTNotification</span> -Objekt, das sich direkt auf diese Benachrichtigung auswirkte. Ein Beispiel ist eine Benachrichtigung über einen Fehler beim Einfügen von Anzeigen, der direkt einem Einfügekonflikt zwischen Zeitlinien entspricht. Nicht alle Benachrichtigungen enthalten eine innere Benachrichtigung. </td> 
  </tr> 
 </tbody> 
</table>
