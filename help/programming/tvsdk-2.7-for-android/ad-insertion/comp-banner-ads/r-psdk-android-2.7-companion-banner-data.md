---
description: Der Inhalt eines AdAsset beschreibt ein begleitendes Banner.
title: Companion-Bannerdaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Companion-Bannerdaten {#companion-banner-data}

Der Inhalt eines AdAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Jeder `AdAsset` enthält Informationen zum Anzeigen des Assets.

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
   <td colname="col2"> Breite des begleitenden Banners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Höhe des begleitenden Banners in Pixel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ressourcentyp </td> 
   <td colname="col2">Der Ressourcentyp für dieses begleitende Banner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: Die Daten befinden sich im HTML-Code. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: Die Daten sind eine iFrame-URL (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Manchmal verfügt das begleitende Banner auch über eine <span class="codeph"> staticURL</span> die eine direkte URL zum Bild oder zu einer <span class="codeph"> .swf</span> (Flash-Banner). </p> <p>Wenn Sie HTML oder iframe nicht verwenden möchten, können Sie stattdessen eine direkte URL zu einem Bild oder SWF verwenden, um das Banner in der Flash-Bühne anzuzeigen. In diesem Fall können Sie die <span class="codeph"> staticURL</span> , um das Banner anzuzeigen. </p> <p>Wichtig: Sie müssen überprüfen, ob die statische URL eine gültige Zeichenfolge ist, da diese Eigenschaft möglicherweise nicht immer verfügbar ist. </p> </td> 
  </tr> 
 </tbody> 
</table>
