---
description: Sie können mehrere Optionen für die Formatierung von Beschriftungen festlegen. Diese Optionen setzen die Stiloptionen in den Originalbeschriftungen außer Kraft.
title: Gestaltungsoptionen für Bildunterschriften
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Stiloptionen für Untertitel{#closed-caption-styling-options}

Sie können mehrere Optionen für die Formatierung von Beschriftungen festlegen. Diese Optionen setzen die Stiloptionen in den Originalbeschriftungen außer Kraft.

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
>In Optionen, die Standardwerte definieren (z. B. `DEFAULT`), bezieht sich dieser Wert auf die Einstellung, die bei der ursprünglichen Angabe der Beschriftung festgelegt wurde.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Format </th> 
   <th colname="2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Schrift </td> 
   <td colname="2"> <p>Der Schrifttyp. </p> <p>Kann nur auf einen Wert eingestellt werden, der von der Auflistung <span class="codeph"> TextFormat.Font </span> definiert wird und beispielsweise mit oder ohne Serifen konstatiert ist. </p> <p>Tipp:  Die tatsächlichen Schriftarten, die auf einem Gerät verfügbar sind, können variieren und bei Bedarf werden Ersatzschriften verwendet. Monospace mit Serifen wird normalerweise als Ersatz verwendet, obwohl diese Ersetzung systemspezifisch sein kann. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Größe </td> 
   <td colname="2"> <p>Die Größe der Beschriftung. </p> <p> Kann nur auf einen Wert eingestellt werden, der von der Auflistung <span class="codeph"> TextFormat.Size </span> definiert wird: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM  </span> - Standardgröße </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROSS  </span> - Ca. 30% größer als mittel </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN  </span> - Ca. 30 % kleiner als mittel </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDARD  </span> - Die Standardgröße für die Beschriftung; gleich mittel </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftfarbe </td> 
   <td colname="2"> <p>Die Schriftfarbe. </p> <p>Kann nur auf einen Wert eingestellt werden, der von der Auflistung <span class="codeph"> TextFormat.Color </span> definiert wird. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Hintergrundfarbe </td> 
   <td colname="2"> <p>Die Farbe der Hintergrundzeichenzelle. </p> <p>Kann nur auf Werte eingestellt werden, die für die Schriftfarbe verfügbar sind. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Schriftdeckkraft </td> 
   <td colname="2"> <p>Die Deckkraft des Textes. </p> <p>Wird als Prozentsatz von 0 (vollständig transparent) bis 100 (vollständig undurchsichtig) ausgedrückt. <span class="codeph"> DEFAULT_OPACITY  </span> für die Schriftart ist 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> untere Vertiefung </td> 
   <td colname="2"> <p>Vertikaler Abstand vom unteren Rand des Beschriftungsfensters, um Beschriftungen zu vermeiden. </p> <p>Wird als Prozentsatz der Höhe des Beschriftungsfensters (z. B. "20 %") oder als Anzahl von Pixeln (z. B. "20") angegeben. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Sicherer Bereich </td> 
   <td colname="2"> <p>Ein Bereich um den Rand des Bildschirms zwischen 0 % und 25 %, in dem keine Beschriftungen angezeigt werden. </p> <p>Standardmäßig beträgt der sichere Bereich für 608/708 12 % und der sichere Bereich für WebVTT 0 %. Diese Einstellung ermöglicht es Ihrer Anwendung, diese Standardeinstellung zu überschreiben. Wenn zwei Werte angegeben werden, z. B. die Zeichenfolge "10 %,20 %", ist der erste Wert der horizontale sichere Bereich und der zweite Wert der vertikale sichere Bereich. Wenn ein Wert angegeben wird, z. B. die Zeichenfolge "15 %", verwenden sowohl die vertikale als auch die horizontale Achse den angegebenen sicheren Bereich. </p> </td> 
  </tr> 
 </tbody> 
</table>

