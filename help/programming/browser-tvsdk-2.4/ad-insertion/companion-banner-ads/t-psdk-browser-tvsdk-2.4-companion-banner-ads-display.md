---
description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass Browser TVSDK auf anzeigenbezogene Ereignisse überwacht.
title: Anzeigen von Banneranzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass Browser TVSDK auf anzeigenbezogene Ereignisse überwacht.

Browser TVSDK bietet eine Liste mit begleitenden Banneranzeigen, die einer linearen Anzeige über die `AdobePSDK.PSDKEventType.AD_STARTED` -Ereignis.

Manifeste können begleitende Banneranzeigen wie folgt spezifizieren:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL eines statischen Bildes oder einer Adobe-Flash-SWF-Datei

Für jede begleitende Anzeige zeigt Browser TVSDK an, welche Typen für Ihre Anwendung verfügbar sind.

Hinzufügen eines Listeners für das Ereignis `AdobePSDK.PSDKEventType.AD_STARTED` das Folgendes bewirkt:
1. Löscht vorhandene Anzeigen in der Bannerinstanz.
1. Ruft die Liste der begleitenden Anzeigen von ab `Ad.getCompanionAssets`.
1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, navigieren Sie für Bannerinstanzen über die Liste.

   Jede Bannerinstanz (eine `AdBannerAsset`) Informationen wie Breite, Höhe, Ressourcentyp (HTML, iframe oder statisch) sowie Daten enthält, die zum Anzeigen des begleitenden Banners erforderlich sind.
1. Wenn für eine Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.
1. Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Stelle anzeigt.

   Dies ist normalerweise ein `div`und Ihre -Funktion verwendet die `div ID` , um das Banner anzuzeigen. Beispiel:

   Fügen Sie den Ereignis-Listener hinzu:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implementieren Sie den Listener-Handler:

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void 
   { 
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
   function displayCompanion (resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
       var bannerDiv = document.getElementById('banner' + width + 'x' + height);  
   
       // Assuming that there is an HTML element on the page  
       // with an id of "banner300x250", for example 
       if (bannerDiv !== null) { 
           bannerDiv.innerHTML = data; 
       } 
   }
   ```
