---
description: Diese Klassen liefern Informationen über die Zeitleiste des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.
title: Timeline-Klassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Timeline-Klassen{#timeline-classes}

Diese Klassen liefern Informationen über die Zeitleiste des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.

Package: [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> <p>Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/PlacementOpportunity.html" format="html" scope="external"> PlacementOpportunity</a></span> </td> 
   <td colname="2"> Eine Opportunity-Klasse stellt einen Zielpunkt auf der Timeline dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Timeline</a> </td> 
   <td colname="2"> Schnittstelle, die einen Iterator für die Verarbeitung von Timeline-Markern bereitstellt. Stellt die Timeline des Inhalts dar, einschließlich Werbeunterbrechungen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem</a> </span> </td> 
   <td colname="2"> Klasse. Generische, unveränderliche Darstellung eines Timeline-Elements. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker</a> </span> </td> 
   <td colname="2"> Schnittstelle, die eine Markierung auf der Timeline darstellt. Dies markiert eine Region von Interesse auf der tatsächlichen Timeline. Derzeit sind die Interessensgebiete die Anzeigen, die Sie beispielsweise mit einer anderen Farbe auf der Benutzeroberfläche der Scrubbing-Leiste markieren möchten. Jede Markierung wird durch eine Position und eine Dauer definiert (jeweils in Millisekunden). </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineOperation.html" format="html" scope="external"> TimelineOperation</a> </td> 
   <td colname="2"> Basisklasse für alle Vorgänge, die sich auf die Timeline auswirken. </td> 
  </tr> 
 </tbody> 
</table>
