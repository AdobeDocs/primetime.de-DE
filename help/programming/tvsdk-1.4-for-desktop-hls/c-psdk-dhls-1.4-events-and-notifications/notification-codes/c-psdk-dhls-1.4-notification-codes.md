---
description: Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.
seo-description: Das TVSDK-Benachrichtigungssystem enthält verschiedene Fehler-, Warn- und Informationshinweise, die diagnostische Metadaten bereitstellen.
seo-title: Benachrichtigungscodes
title: Benachrichtigungscodes
uuid: a7b77a5c-9873-45cf-8499-aa00270a7ad6
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# Übersicht {#notification-codes-overview}

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
   <td colname="1"> type </td> 
   <td colname="2"> Der Benachrichtigungstyp. Abhängig von der Plattform bezieht sich diese Eigenschaft auf einen aufgezählten Typ mit möglichen Werten für INFO, WARN oder ERROR. Dies ist die Gruppierung auf oberster Ebene für Benachrichtigungen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> code </td> 
   <td colname="2">Die der Benachrichtigung zugewiesene numerische Darstellung: 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">Ereignisse zur Fehlermeldung von 100000 bis 19999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">Ereignis für die Meldung von Warnmeldungen von 20000 bis 29999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">Ereignis für die Information von 300000 bis 399999 </li> 
    </ul> <p>Jeder Bereich auf der obersten Ebene, z. B. Fehler, wird in Unterbereiche unterteilt, wie z. B. 101000 bis 101999, die Wiedergabefehler darstellen. </p>
    <pre>
     Die Auflistung 
     <span class="codeph"> mediacore.PSDKErrorCode</span> Listen der möglichen Werte.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> name </td> 
   <td colname="2">Eine Zeichenfolge, die eine für Menschen lesbare Beschreibung des Codes enthält, z. B. <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> metadata </td> 
   <td colname="2">Schlüssel/Wert-Paare, die zusätzliche relevante Informationen zur Benachrichtigung enthalten. Beispielsweise würde ein Schlüssel mit dem Namen <span class="codeph"> URL</span> mit einem Wert verknüpft, der eine URL im Zusammenhang mit der Benachrichtigung ist, z. B. eine ungültige URL, die einen Fehler verursachte. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> innerNotification </td> 
   <td colname="2">Ein Verweis auf ein anderes <span class="codeph">-MediaPlayerNotification</span>-Objekt, das diese Benachrichtigung direkt beeinflusste. Ein Beispiel könnte eine Benachrichtigung über einen Fehler beim Einfügen von Anzeigen sein, der direkt einem Einfügekonflikt in der Zeitleiste entspricht. Nicht alle Benachrichtigungen bieten eine interne Benachrichtigung. </td> 
  </tr> 
 </tbody> 
</table>

