---
description: TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und nach dem Ende der linearen Anzeige oft auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.
title: Banneranzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Begleitbanneranzeigen {#companion-banner-ads}

TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und nach dem Ende der linearen Anzeige oft auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.

Befolgen Sie bei der Anzeige von Begleithandanzeigen die folgenden Empfehlungen:

* Versuchen Sie, so viele Banneranzeigen wie möglich im Layout Ihres Players anzuzeigen.
* Bieten Sie ein begleitendes Banner nur dann an, wenn Sie eine Position haben, die exakt der angegebenen Höhe und Breite entspricht.

   >[!TIP]
   >
   >Ändern Sie die Größe des Banners nicht.

* Präsentieren Sie die begleitenden Banner so bald wie möglich nach Beginn der Anzeige.
* Überlagern Sie den Haupt-Anzeigen-/Video-Container nicht mit begleitenden Bannern.
* Anzeigen von Begleit-Bannern nach Ende der Anzeige fortsetzen.

   Der Standard besteht darin, jedes Begleitbanner anzuzeigen, bis Sie einen Ersatz für dieses Banner haben.

## Begleitbannerdaten {#companion-banner-data}

Der Inhalt eines AdBannerAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Das `AdPlaybackEvent.AD_STARTED`-Ereignis gibt eine `Ad`-Instanz zurück, die eine `companionAssets`-Eigenschaft ( `Vector.<AdAsset>`) enthält.
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
   <td colname="col1"> Bannerdaten </td> 
   <td colname="col2"> Die Daten des Typs, der von <span class="codeph"> resourceType</span> für dieses begleitende Banner angegeben wird. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Manchmal verfügt das Begleitbanner auch über eine statische URL, die eine direkte URL zum Bild oder zu einer <span class="filepath"> .swf</span> (Flash-Banner) darstellt. </p> <p>Wenn Sie kein HTML oder iframe verwenden möchten, können Sie eine direkte URL zu einem Flash oder einer SWF verwenden, um das Banner stattdessen im Anzeigebereich ""anzuzeigen. In diesem Fall können Sie die staticURL verwenden, um das Banner anzuzeigen. </p> <p>Wichtig:  Sie müssen überprüfen, ob die statische URL eine gültige Zeichenfolge ist, da diese Eigenschaft möglicherweise nicht immer verfügbar ist. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und TVSDK erlauben, auf anzeigenbezogene Ereignis zu hören.

TVSDK bietet eine Liste von begleitenden Banneranzeigen, die über das `AdPlaybackEvent.AD_STARTED`-Ereignis-Ereignis mit einer linearen Anzeige verknüpft sind.

Manifeste können begleitende Banneranzeigen wie folgt angeben:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL einer statischen Bilddatei oder einer Flash-SWF-Datei einer Adobe

Für jede Begleitanzeige gibt TVSDK an, welche Typen für Ihre Anwendung verfügbar sind.

hinzufügen Sie einen Listener für das `AdPlaybackEvent.AD_STARTED`-Ereignis, das Folgendes ausführt:

1. Löscht vorhandene Anzeigen in der Bannerinstanz.

1. Ruft die Liste der begleitenden Anzeigen von `Ad.companionAssets` ab.

1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, müssen Sie die Liste für Bannerinstanzen durchlaufen.

   Jede Bannerinstanz (`AdBannerAsset`) enthält Informationen wie Breite, Höhe, Ressourcentyp (html, iframe oder statisch) und Daten, die zum Anzeigen des begleitenden Banners erforderlich sind.

1. Wenn bei einer Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.

   Um eine eigenständige Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP (DoubleClick for Publishers)-Display-Tag in der entsprechenden Bannerinstanz auszuführen.

1. Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, üblicherweise JavaScript, indem `ExternalInterface` verwendet wird, die die Banner an einer geeigneten Position anzeigt.

   Dies ist normalerweise ein `div` und Ihre Funktion verwendet das `div ID`, um das Banner anzuzeigen. Beispiel:

   hinzufügen Ereignis-Listener:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implementieren des Listener-Handlers:

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void { 
       // check if there are any companion banner 
       if (event.ad && event.ad.companionAssets  
                    && event.ad.companionAssets.length > 0) { 
           for each (var banner:AdBannerAsset in event.ad.companionAssets) { 
               if (ExternalInterface.available) { 
                   //-- call the java script that will handle the banner display. 
                   ExternalInterface.call('addBanner', banner.resourceType,  
                       banner.width, banner.height, banner.bannerData); 
               } 
           } 
       }  
       //...        
   }
   ```

   Beispiel für JavaScript zur Verarbeitung der Anzeige:

   ```js
   function addBanner(resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
   
   //Assume an html element on the page with id like 'banner300x250' 
       var bannerDiv = document.getElementById('banner' + width +  
           'x' + height);  
       if (bannerDiv != null) { 
           if (resourceType == "html") { // for html resource 
               bannerDiv.innerHTML = data; 
           } 
           else if (resourceType == "iframe") { // for iframe resource 
               bannerDiv.innerHTML = "<iframe src='" + data +  
                   "' width='100%' height='100%'></iframe>"; 
           } 
       } 
   }
   ```
