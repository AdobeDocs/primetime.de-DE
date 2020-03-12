---
description: TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.
seo-description: TVSDK bietet Klassen und Methoden, mit denen Sie das Wiedergabeverhalten von Inhalten, die Werbung enthalten, anpassen können.
seo-title: API-Elemente für die Anzeigenwiedergabe
title: API-Elemente für die Anzeigenwiedergabe
uuid: 5e21e709-8446-4fed-8711-aa4f629f1147
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# API-Elemente für die Anzeigenwiedergabe {#api-elements-for-ad-playback}

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
   <td colname="col1"><span class="apiname"> AdvertisingMetadata </span> </td> 
   <td colname="col2">Legen Sie fest, ob eine Werbeunterbrechung als von einem Viewer gesehen gekennzeichnet werden soll, und wann, wenn ja, wann sie markiert werden soll. Legen Sie die überwachte Richtlinie mit <span class="codeph"> setAdBreakAsWatched</span> und <span class="codeph"> getAdBreakAsWatched</span>fest und rufen Sie sie ab. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Listet mögliche Wiedergaberichtlinien für Werbeunterbrechungen auf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdPolicy</span> </td> 
   <td colname="col2"> Listet mögliche Wiedergaberichtlinien für Anzeigen auf. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdPolicySelector </span> </td> 
   <td colname="col2"> Schnittstelle, die die Anpassung des TVSDK Anzeigenverhaltens ermöglicht. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> DefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Klasse, die das standardmäßige TVSDK-Verhalten implementiert. Ihre Anwendung kann diese Klasse außer Kraft setzen, um das Standardverhalten anzupassen, ohne die vollständige Schnittstelle zu implementieren. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="apiname"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span> <p>Dies ist die lokale Zeit der Wiedergabe, wobei die platzierten Werbeunterbrechungen ausgeschlossen werden. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> searchingToLocal</span>. <p>Hier erfolgt die Suche relativ zu einer lokalen Zeit im Stream. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>Die virtuelle Position auf der Zeitleiste wird in die lokale Position umgewandelt. </p> </li> 
    </ul> <p>Wichtig:  " <span class="codeph"> getLocalTime</span> "in <span class="codeph"> MediaPlayer</span> gibt die aktuelle Zeit relativ zum ursprünglichen Inhalt zurück, ohne dynamisch geteilte Anzeigen. <span class="codeph"> getLocalTime</span> in <span class="codeph"> AdBreak</span> gibt den Beginn der Unterbrechung relativ zum Originalinhalt zurück. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatched</span> -Eigenschaft. Gibt an, ob der Viewer die Anzeige gesehen hat. </td> 
  </tr> 
 </tbody> 
</table>

