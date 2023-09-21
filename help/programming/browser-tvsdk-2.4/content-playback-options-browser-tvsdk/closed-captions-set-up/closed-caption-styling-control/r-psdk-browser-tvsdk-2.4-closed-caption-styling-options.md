---
description: Sie können mehrere Beschriftungsstil-Optionen festlegen. Diese Optionen überschreiben die Stiloptionen in den Originalbeschriftungen.
title: Stiloptionen für geschlossene Beschriftungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Stiloptionen für geschlossene Beschriftungen{#closed-caption-styling-options}

Sie können mehrere Beschriftungsstil-Optionen festlegen. Diese Optionen überschreiben die Stiloptionen in den Originalbeschriftungen.

```js
new TextFormat( 
   font,  
   fontColor,  
   edgeColor,  
   fontEdge,  
   backgroundColor,  
   fillColor,  
   size,  
   fontOpacity,  
   backgroundOpacity,  
   fillOpacity, 
   bottomInset, 
   safeArea) 
```

>[!TIP]
>
>In Optionen, die Standardwerte definieren (z. B. `DEFAULT`), bezieht sich dieser Wert auf die Einstellung, als die Beschriftung ursprünglich angegeben wurde.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Format </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftart </td> 
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Kann nur auf einen Wert festgelegt werden, der durch die Variable <span class="codeph"> TextFormat.Font </span> -Auflistung und stellt z. B. mit oder ohne Serifen einen Abstand dar. </p> <p>Tipp: Die tatsächlichen Schriftarten, die auf einem Gerät verfügbar sind, können variieren und bei Bedarf werden Ersatzschriften verwendet. Monospace mit Serifen wird in der Regel als Ersatz verwendet, obwohl diese Substitution systemspezifisch sein kann. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Größe </td> 
   <td colname="2"> <p>Die Größe der Beschriftung. </p> <p> Kann nur auf einen Wert gesetzt werden, der durch die Variable <span class="codeph"> TextFormat.Size </span> Auflistung: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - Standardgröße </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROSS </span> - Etwa 30% größer als mittel </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN </span> - Etwa 30% kleiner als mittel </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDARD </span> - Die Standardgröße für die Beschriftung; identisch mit Medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftfarbe </td> 
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Kann nur auf einen Wert gesetzt werden, der durch die Variable <span class="codeph"> TextFormat.Color </span> -Auflistung. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrundfarbe </td> 
   <td colname="2"> <p>Die Hintergrundfarbe der Zeichenzelle. </p> <p>Kann nur auf Werte gesetzt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftdeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Textes. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig opak) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY </span> für die Schriftart 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> untere Einrückung </td> 
   <td colname="2"> <p>Vertikaler Abstand vom unteren Rand des Beschriftungsfensters, um Beschriftungen zu vermeiden. </p> <p>Wird als Prozentsatz der Höhe des Beschriftungsfensters (z. B. "20 %") oder als Anzahl von Pixeln (z. B. "20") ausgedrückt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Sicherheitsbereich </td> 
   <td colname="2"> <p>Ein Bereich um den Bildschirmrand zwischen 0 % und 25 %, in dem keine Beschriftungen angezeigt werden. </p> <p>Standardmäßig beträgt der sichere Bereich für 608/708 12 % und der sichere Bereich für WebVTT 0 %. Mit dieser Einstellung kann Ihre Anwendung diesen Standard überschreiben. Wenn zwei Werte angegeben werden, z. B. die Zeichenfolge "10 %,20 %", ist der erste Wert der horizontale sichere Bereich und der zweite Wert der vertikale sichere Bereich. Wenn ein Wert angegeben wird, z. B. die Zeichenfolge "15%", verwenden sowohl die vertikale als auch die horizontale Achse den angegebenen sicheren Bereich. </p> </td> 
  </tr> 
 </tbody> 
</table>
