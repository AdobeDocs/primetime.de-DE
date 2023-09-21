---
description: TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und häufig nach dem Ende der linearen Anzeige auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.
title: Companion-Banneranzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Companion-Banneranzeigen {#companion-banner-ads}

TVSDK unterstützt begleitende Banneranzeigen, bei denen es sich um Anzeigen handelt, die eine lineare Anzeige begleiten und häufig nach dem Ende der linearen Anzeige auf der Seite bleiben. Ihre Anwendung ist für die Anzeige der begleitenden Banner verantwortlich, die mit einer linearen Anzeige bereitgestellt werden.

Befolgen Sie beim Anzeigen von begleitenden Anzeigen die folgenden Empfehlungen:

* Versuchen Sie, so viele begleitende Banneranzeigen einer Videoanzeige wie im Layout Ihres Players verfügbar zu machen.
* Zeigen Sie ein begleitendes Banner nur dann an, wenn Sie eine Position haben, die genau der angegebenen Höhe und Breite entspricht.

  >[!TIP]
  >
  >Ändern Sie die Größe des Banners nicht.

* Präsentieren Sie die begleitenden Banner so bald wie möglich nach Beginn der Anzeige.
* Überlagern Sie den Haupt-Anzeigen-/Video-Container nicht mit begleitenden Bannern.
* Anzeigen von begleitenden Bannern nach Ende der Anzeige

  Die Standardeinstellung besteht darin, jedes begleitende Banner anzuzeigen, bis Sie einen Ersatz für dieses Banner haben.

## Companion-Bannerdaten {#companion-banner-data}

Der Inhalt eines AdBannerAsset beschreibt ein begleitendes Banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Die `AdPlaybackEvent.AD_STARTED` -Ereignis gibt eine `Ad` -Instanz, die `companionAssets` Eigenschaft ( `Vector.<AdAsset>`).
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
   <td colname="col1"> Bannerdaten </td> 
   <td colname="col2"> Die Daten des Typs, der durch <span class="codeph"> resourceType</span> für dieses begleitende Banner. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Manchmal verfügt das begleitende Banner auch über eine staticURL, die eine direkte URL zum Bild oder zu einer <span class="filepath"> .swf</span> (Flash-Banner). </p> <p>Wenn Sie HTML oder iframe nicht verwenden möchten, können Sie stattdessen eine direkte URL zu einem Bild oder SWF verwenden, um das Banner in der Flash-Bühne anzuzeigen. In diesem Fall können Sie die staticURL verwenden, um das Banner anzuzeigen. </p> <p>Wichtig: Sie müssen überprüfen, ob die statische URL eine gültige Zeichenfolge ist, da diese Eigenschaft möglicherweise nicht immer verfügbar ist. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass TVSDK auf anzeigenbezogene Ereignisse überwacht.

TVSDK bietet eine Liste mit begleitenden Banneranzeigen, die über die `AdPlaybackEvent.AD_STARTED` -Ereignis.

Manifeste können begleitende Banneranzeigen wie folgt spezifizieren:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL eines statischen Bildes oder einer Adobe-Flash-SWF-Datei

TVSDK gibt für jede begleitende Anzeige an, welche Typen für Ihre Anwendung verfügbar sind.

Fügen Sie einen Listener für die `AdPlaybackEvent.AD_STARTED` -Ereignis, das Folgendes ausführt:

1. Löscht vorhandene Anzeigen in der Bannerinstanz.

1. Ruft die Liste der begleitenden Anzeigen von ab `Ad.companionAssets`.

1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, navigieren Sie für Bannerinstanzen über die Liste.

   Jede Bannerinstanz ( `AdBannerAsset`) Informationen wie Breite, Höhe, Ressourcentyp (HTML, iframe oder statisch) sowie Daten enthält, die zum Anzeigen des begleitenden Banners erforderlich sind.

1. Wenn für eine Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.

   Um eine eigenständige Display-Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP-Display-Anzeigen-Tag (DoubleClick for Publishers) in der entsprechenden Bannerinstanz auszuführen.

1. Sendet die Bannerinformationen mithilfe von an eine Funktion auf Ihrer Seite (meist JavaScript) `ExternalInterface`, das die Banner an einer geeigneten Stelle anzeigt.

   Dies ist normalerweise ein `div`und Ihre -Funktion verwendet die `div ID` , um das Banner anzuzeigen. Beispiel:

   Fügen Sie den Ereignis-Listener hinzu:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implementieren Sie den Listener-Handler:

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
