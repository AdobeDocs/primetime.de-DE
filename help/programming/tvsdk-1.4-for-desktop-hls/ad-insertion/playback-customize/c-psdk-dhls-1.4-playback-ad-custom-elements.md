---
description: TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.
seo-description: TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.
seo-title: API-Elemente für die Anzeigenwiedergabe
title: API-Elemente für die Anzeigenwiedergabe
uuid: 61ebbfd7-696c-4a5b-8dbb-682770cd5840
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# API-Elemente für die Anzeigenwiedergabe{#api-elements-for-ad-playback}

TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.

Die folgenden API-Elemente eignen sich zum Anpassen der Wiedergabe:

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API-Element </th> 
   <th colname="col2" class="entry"> Inhalte, die Werbung unterstützen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdvertisingMetadata</span> </td> 
   <td colname="col2">Legen Sie fest, ob eine Werbeunterbrechung als von einem Viewer gesehen gekennzeichnet werden soll, und wann, wenn ja, wann sie markiert werden soll. Überwachte Richtlinie festlegen und abrufen mit 
    <ph>
     die <span class="codeph"> Eigenschaft adBreakAsWatched</span> .
    </ph> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Listet mögliche Wiedergaberichtlinien für Werbeunterbrechungen auf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicy</span> </td> 
   <td colname="col2"> Listet mögliche Wiedergaberichtlinien für Anzeigen auf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicySelector</span> </td> 
   <td colname="col2"> Schnittstelle, die die Anpassung des TVSDK Anzeigenverhaltens ermöglicht. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DefaultAdPolicySelector</span> </td> 
   <td colname="col2"> Klasse, die das standardmäßige TVSDK-Verhalten implementiert. Ihre Anwendung kann diese Klasse außer Kraft setzen, um das Standardverhalten anzupassen, ohne die vollständige Schnittstelle zu implementieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> localTime</span>. <p>Dies ist die lokale Zeit der Wiedergabe, wobei die platzierten Werbeunterbrechungen ausgeschlossen werden. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchingToLocal</span>. <p>Hier erfolgt die Suche relativ zu einer lokalen Zeit im Stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>Die virtuelle Position auf der Zeitleiste wird in die lokale Position umgewandelt. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TimelineItem</span> </td> 
   <td colname="col2"> 
    <ul id="ul_99AD34F823DB4F10937EE39DAD0C0B72"> 
     <li id="li_87E2DA15ECE74CFE9C9FBBE8F4B62440"><span class="codeph"> überwacht</span>. <p>Gibt an, ob der Viewer die Anzeige gesehen hat. </p> </li> 
     <li id="li_A9E5A9CF701C48BC94C93F28C114778D"><span class="codeph"> localRange</span>. <p>Die Anfangsposition und die Dauer einer Werbeunterbrechung oder Anzeige relativ zum ursprünglichen Inhalt. </p> </li> 
     <li id="li_070BDA0BF4184863AF44652BD5A0CCEC"><span class="codeph"> virtualRange</span>. <p>Die Startposition und die Dauer einer Werbeunterbrechung oder Anzeige in der virtuellen Zeitleiste, nachdem alle Platzierungen der Anzeige berücksichtigt wurden. </p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

