---
description: Diese Klassen liefern Informationen über die Zeitleiste des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.
title: Timeline-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Timeline-Klassen{#timeline-classes}

Diese Klassen liefern Informationen über die Zeitleiste des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.

Package: [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> <p>Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker </a> </span> </td> 
   <td colname="2"> Schnittstelle, die das Protokoll definiert, das Sie implementieren müssen, wenn Sie ein Content-Tracking-Modul erstellen möchten, das zur Integration in die TVSDK-Bibliothek entwickelt wurde. <p>Für diese Schnittstelle müssen Sie festlegen, wie Fortschrittsereignisse dem Remote-Tracking-System gemeldet werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> Chancen </a> </span> </td> 
   <td colname="2"> Basisklasse für alle Opportunitätsklassen. Eine Opportunity-Klasse stellt einen "interessanten"Punkt auf der Timeline dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> Platzierung </a> </span> </td> 
   <td colname="2"> Klasse, die Informationen zur Timeline-Platzierung umschließt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode </a> </span> </td> 
   <td colname="2"> Auflistung der Platzierungsmodi, z. B. ob Inhalte eingefügt oder ersetzt werden sollen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType </a> </span> </td> 
   <td colname="2"> Auflistung der Platzierungstypen, die angeben, wo die Platzierung in der Timeline vorgenommen wird, z. B. PRE_ROLL. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> Reservierung </a> </span> </td> 
   <td colname="2"> Eine Reservierung wird verwendet, um eine weitere Verarbeitung eines bestimmten Zeitbereichs in der Zeitleiste zu beschränken oder zu verhindern. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Timeline </a> </span> </td> 
   <td colname="2"> Schnittstelle, die einen Iterator für die Verarbeitung von Timeline-Markern bereitstellt. Stellt die Timeline des Inhalts dar, einschließlich Werbeunterbrechungen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem </a> </span> </td> 
   <td colname="2"> Klasse. Generische, unveränderliche Darstellung eines Timeline-Elements. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker </a> </span> </td> 
   <td colname="2"> Klasse, die eine Markierung auf der Timeline darstellt. Dies markiert eine Region von Interesse auf der tatsächlichen Timeline. Derzeit sind die Interessensgebiete die Anzeigen, die Sie beispielsweise mit einer anderen Farbe auf der Benutzeroberfläche der Scrubbing-Leiste markieren möchten. Jede Markierung wird durch eine Position und eine Dauer definiert (jeweils in Millisekunden). </td> 
  </tr> 
 </tbody> 
</table>
