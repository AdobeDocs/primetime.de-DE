---
description: Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.
seo-description: Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.
seo-title: Benachrichtigungscodes
title: Benachrichtigungscodes
uuid: edbce737-28fd-4309-be5a-2e33fcc156b6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Benachrichtigungscodes{#notification-codes}

Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.

Benachrichtigungsobjekte liefern Informationen zum Status des Players. TVSDK stellt eine chronologisch sortierte Liste von Benachrichtigungsobjekten bereit. Jede Benachrichtigung enthält die folgenden Metadaten:

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
   <td colname="2">Der Benachrichtigungstyp. Abhängig von der Plattform bezieht sich diese Eigenschaft auf einen aufgezählten Typ mit möglichen Werten für <span class="codeph"> INFO</span>, <span class="codeph"> WARN</span>oder <span class="codeph"> ERROR</span>. Dies ist die Gruppierung auf oberster Ebene für Benachrichtigungen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span> </td> 
   <td colname="2">Die der Benachrichtigung zugewiesene numerische Darstellung: 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">Ereignisse zur Fehlermeldung von 100000 bis 19999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">Ereignis für die Meldung von Warnmeldungen von 20000 bis 29999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">Ereignis für die Information von 300000 bis 399999 </li> 
    </ul> <p>Jeder Bereich auf der obersten Ebene, z. B. Fehler, wird in Unterbereiche unterteilt, wie z. B. 101000 bis 101999, die Wiedergabefehler darstellen. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Eine Zeichenfolge, die eine für Menschen lesbare Beschreibung des Codes enthält, z. B. <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2">Schlüssel/Wert-Paare, die zusätzliche relevante Informationen zur Benachrichtigung enthalten. Beispielsweise würde ein Schlüssel mit dem Namen <span class="codeph"> URL</span> mit einem Wert verknüpft, der eine URL im Zusammenhang mit der Benachrichtigung ist, z. B. eine ungültige URL, die einen Fehler verursacht hat. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2">Ein Verweis auf ein anderes <span class="codeph"> MediaPlayerNotification</span> -Objekt, das diese Benachrichtigung direkt beeinflusste. Ein Beispiel könnte eine Benachrichtigung über einen Fehler beim Einfügen von Anzeigen sein, der direkt einem Einfügekonflikt in der Zeitleiste entspricht. Nicht alle Benachrichtigungen bieten eine interne Benachrichtigung. </td> 
  </tr> 
 </tbody> 
</table>

