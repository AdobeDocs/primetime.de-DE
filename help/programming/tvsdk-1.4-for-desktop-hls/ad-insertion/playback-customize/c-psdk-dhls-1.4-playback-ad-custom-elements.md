---
description: TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalt anpassen können, der Werbung enthält.
title: API-Elemente für die Anzeigenwiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# API-Elemente für die Anzeigenwiedergabe{#api-elements-for-ad-playback}

TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalt anpassen können, der Werbung enthält.

Die folgenden API-Elemente sind zum Anpassen der Wiedergabe nützlich:

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
   <td colname="col2">Legen Sie fest, ob eine Werbeunterbrechung von einem Viewer als überwacht markiert werden soll und wann sie mit einer Markierung versehen werden soll. Überwachte Richtlinie mithilfe von festlegen und abrufen 
    <pre>
     die 
     <span class="codeph"> adBreakAsWatched</span> -Eigenschaft.
    </pre> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Auflistet mögliche Wiedergaberichtlinien für Werbeunterbrechungen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicy</span> </td> 
   <td colname="col2"> Auflistet mögliche Wiedergaberichtlinien für Anzeigen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicySelector</span> </td> 
   <td colname="col2"> Schnittstelle, die die Anpassung des TVSDK-Anzeigenverhaltens ermöglicht. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DefaultAdPolicySelector</span> </td> 
   <td colname="col2"> Klasse, die das standardmäßige TVSDK-Verhalten implementiert. Ihre Anwendung kann diese Klasse überschreiben, um das Standardverhalten anzupassen, ohne die vollständige Benutzeroberfläche zu implementieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> localTime</span>. <p>Dies ist die lokale Zeit der Wiedergabe ohne die platzierten Werbeunterbrechungen. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchToLocal</span>. <p>Hier erfolgt die Suche relativ zu einer lokalen Zeit im Stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>Die virtuelle Position auf der Timeline wird in die lokale Position konvertiert. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TimelineItem</span> </td> 
   <td colname="col2"> 
    <ul id="ul_99AD34F823DB4F10937EE39DAD0C0B72"> 
     <li id="li_87E2DA15ECE74CFE9C9FBBE8F4B62440"><span class="codeph"> überwachte</span>. <p>Gibt an, ob der Viewer die Anzeige gesehen hat. </p> </li> 
     <li id="li_A9E5A9CF701C48BC94C93F28C114778D"><span class="codeph"> localRange</span>. <p>Die Startposition und die Dauer einer Werbeunterbrechung oder Anzeige in Relation zum ursprünglichen Inhalt. </p> </li> 
     <li id="li_070BDA0BF4184863AF44652BD5A0CCEC"><span class="codeph"> virtualRange</span>. <p>Die Startposition und die Dauer einer Werbeunterbrechung oder Anzeige in der virtuellen Timeline nach Berücksichtigung aller platzierten Werbeunterbrechungen. </p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
