---
description: Der TVSDK-Player sendet Ereignis, um den Status zum Laden benutzerdefinierter Anzeigen anzuzeigen oder eine Anzeige zu ignorieren, die zu lange dauert oder Fehler aufweist. Diese Ereignis werden in Ereignisses.CustomAdEvents definiert.
title: Benutzerdefinierte Ereignisse für Werbeanzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Benutzerspezifische AnzeigenEreignis{#custom-ad-events}

Der TVSDK-Player sendet Ereignis, um den Status zum Laden benutzerdefinierter Anzeigen anzuzeigen oder eine Anzeige zu ignorieren, die zu lange dauert oder Fehler aufweist. Diese Ereignis werden in Ereignisses.CustomAdEvents definiert.

<table id="table_718700E0F0B042F882ED131F79E01D4E"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ereignis </th> 
   <th colname="col2" class="entry"> Definition </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdClickThru  </span> </td> 
   <td colname="col2"> Die Häufigkeit, mit der der Viewer auf eine benutzerdefinierte Anzeige geklickt hat. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError  </span> </td> 
   <td colname="col2"> Bei der benutzerdefinierten Anzeige ist ein Fehler aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded  </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde geladen.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading  </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wird geladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused  </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde angehalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed  </span> </td> 
   <td colname="col2"> Die Wiedergabe der benutzerdefinierten Anzeige wurde nach einer Pause fortgesetzt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPlaying  </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wird abgespielt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress  </span> </td> 
   <td colname="col2"> <p>Der benutzerdefinierte Anzeigenplayer benachrichtigt den TVSDK-Player über den Fortschritt der benutzerdefinierten Anzeige. &amp;nbsp; </p> <p>Die Werte <span class="codeph"> currentTime </span> und <span class="codeph"> totalTime </span> der Anzeige werden mit diesem Ereignis übergeben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde gestartet und wird dem Viewer angezeigt.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStopped </td> 
   <td colname="col2"> Die Wiedergabe der benutzerdefinierten Anzeige ist abgeschlossen. </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->

