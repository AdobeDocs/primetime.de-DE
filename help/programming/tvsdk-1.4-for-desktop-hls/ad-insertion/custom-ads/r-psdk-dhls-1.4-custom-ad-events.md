---
description: Der TVSDK-Player sendet Ereignisse, um den Status des Ladens benutzerdefinierter Anzeigen anzuzeigen oder eine Anzeige zu ignorieren, die zum Laden zu lange dauert oder Fehler aufweist. Diese Ereignisse werden in "events.CustomAdEvents"definiert.
title: Benutzerspezifische Anzeigenereignisse
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Benutzerspezifische Anzeigenereignisse{#custom-ad-events}

Der TVSDK-Player sendet Ereignisse, um den Status des Ladens benutzerdefinierter Anzeigen anzuzeigen oder eine Anzeige zu ignorieren, die zum Laden zu lange dauert oder Fehler aufweist. Diese Ereignisse werden in &quot;events.CustomAdEvents&quot;definiert.

<table id="table_718700E0F0B042F882ED131F79E01D4E"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ereignis </th> 
   <th colname="col2" class="entry"> Definition </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdClickThru </span> </td> 
   <td colname="col2"> Die Anzahl der Klicks auf eine benutzerdefinierte Anzeige durch den Viewer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError </span> </td> 
   <td colname="col2"> Bei der benutzerdefinierten Anzeige ist ein Fehler aufgetreten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde geladen.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wird geladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde angehalten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed </span> </td> 
   <td colname="col2"> Die Wiedergabe der benutzerdefinierten Anzeige wurde nach einer Pause fortgesetzt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPlaying </span> </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wird wiedergegeben. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress </span> </td> 
   <td colname="col2"> <p>Der benutzerdefinierte Anzeigen-Player benachrichtigt den TVSDK-Player über den Fortschritt der benutzerdefinierten Anzeige. &amp;nbsp; </p> <p>Die <span class="codeph"> currentTime </span> und <span class="codeph"> totalTime </span> der Anzeige mit diesem Ereignis übergeben werden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> Die benutzerdefinierte Anzeige wurde bereits abgespielt und wird dem Viewer angezeigt.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStopped </td> 
   <td colname="col2"> Die Wiedergabe der benutzerdefinierten Anzeige ist abgeschlossen. </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->
