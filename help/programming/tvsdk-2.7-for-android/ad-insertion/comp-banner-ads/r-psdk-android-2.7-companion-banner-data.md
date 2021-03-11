---
description: Der Inhalt eines AdAsset beschreibt ein begleitendes Banner.
title: Begleitbannerdaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Begleitbannerdaten {#companion-banner-data}

Der Inhalt eines AdAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Jedes `AdAsset` stellt Informationen zum Anzeigen des Assets bereit.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Verfügbare Informationen </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Breite des Begleitbanners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Höhe des Begleitbanners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ressourcentyp </td> 
   <td colname="col2">Der Ressourcentyp für dieses begleitende Banner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: Die Daten sind im HTML-Code enthalten. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: Die Daten sind eine iframe-URL (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Manchmal hat das Begleitbanner auch eine <span class="codeph"> staticURL</span>, die eine direkte URL zum Bild oder zu einer <span class="codeph"> .swf</span> (Flash-Banner) ist. </p> <p>Wenn Sie kein HTML oder iframe verwenden möchten, können Sie eine direkte URL zu einem Flash oder einer SWF verwenden, um das Banner stattdessen im Anzeigebereich ""anzuzeigen. In diesem Fall können Sie die statische URL <span class="codeph"> </span> verwenden, um das Banner anzuzeigen. </p> <p>Wichtig:  Sie müssen überprüfen, ob die statische URL eine gültige Zeichenfolge ist, da diese Eigenschaft möglicherweise nicht immer verfügbar ist. </p> </td> 
  </tr> 
 </tbody> 
</table>

