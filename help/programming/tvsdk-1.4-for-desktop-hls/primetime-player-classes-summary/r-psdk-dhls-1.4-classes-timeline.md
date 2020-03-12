---
description: Diese Klassen bieten Informationen zur Zeitschiene des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.
seo-description: Diese Klassen bieten Informationen zur Zeitschiene des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.
seo-title: Zeitleistenklassen
title: Zeitleistenklassen
uuid: 9c06fec1-d725-4fe8-9cf5-1e3ade2b7d27
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Zeitleistenklassen{#timeline-classes}

Diese Klassen bieten Informationen zur Zeitschiene des jeweiligen Mediums, einschließlich der Platzierung von Anzeigen.

Paket: [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Name </th> 
   <th colname="2" class="entry"> <p>Beschreibung </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker </a></span> </td> 
   <td colname="2"> Schnittstelle, die das Protokoll definiert, das Sie implementieren müssen, wenn Sie ein Content-Tracking-Modul erstellen möchten, das zur Integration mit der TVSDK-Bibliothek entwickelt wurde. <p>Für diese Schnittstelle müssen Sie festlegen, wie Ereignis über den Fortschritt dem Remote-Verfolgungssystem gemeldet werden. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> Chancen </a></span> </td> 
   <td colname="2"> Basisklasse für alle Opportunitätsklassen. Eine Opportunitätsklasse stellt einen "interessanten"Punkt auf der Zeitschiene dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> Platzierung </a></span> </td> 
   <td colname="2"> Klasse, die Informationen zur Platzierung der Zeitschiene umschließt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> Platzierungsmodus </a></span> </td> 
   <td colname="2"> Auflistung der Platzierungsmodi, z. B. ob Inhalte eingefügt oder ersetzt werden sollen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> Platzierungstyp </a></span> </td> 
   <td colname="2"> Auflistung der Platzierungstypen, die angeben, wo die Platzierung in der Zeitschiene erfolgt; zum Beispiel PRE_ROLL. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> Reservierung </a></span> </td> 
   <td colname="2"> Eine Reservierung wird verwendet, um eine weitere Verarbeitung eines bestimmten Zeitraums auf der Zeitschiene zu begrenzen oder zu verhindern. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Zeitschiene </a></span> </td> 
   <td colname="2"> Schnittstelle, die einen Iterator für die Verarbeitung von Zeitschienenmarken bereitstellt. Stellt die Zeitleiste des Inhalts einschließlich Werbeunterbrechungen dar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem </a></span> </td> 
   <td colname="2"> Klasse. Generisch unveränderliche Darstellung eines Zeitschienenelements. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker </a></span> </td> 
   <td colname="2"> Klasse, die eine Markierung auf der Zeitleiste darstellt. Dies kennzeichnet eine Interessensregion auf der tatsächlichen Zeitschiene. Derzeit sind die Interessensgebiete die Anzeigen, die Sie z. B. mit einer anderen Farbe auf der Benutzeroberfläche der Scrubbing-Leiste markieren möchten. Jeder Marker wird durch eine Position und eine Dauer definiert (jeweils in Millisekunden). </td> 
  </tr> 
 </tbody> 
</table>

