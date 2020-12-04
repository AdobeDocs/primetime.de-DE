---
description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass Browser TVSDK auf anzeigenbezogene Ereignis überwacht.
seo-description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass Browser TVSDK auf anzeigenbezogene Ereignis überwacht.
seo-title: Anzeigen von Bannerwerbung
title: Anzeigen von Bannerwerbung
uuid: aabc126e-b3aa-42dd-ab50-a7db8e324c50
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass Browser TVSDK auf anzeigenbezogene Ereignis überwacht.

Browser TVSDK bietet eine Liste von begleitenden Banneranzeigen, die über das `AdobePSDK.PSDKEventType.AD_STARTED`-Ereignis mit einer linearen Anzeige verknüpft sind.

Manifeste können begleitende Banneranzeigen wie folgt angeben:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL einer statischen Bilddatei oder einer Flash-SWF-Datei einer Adobe

Browser TVSDK gibt für jede Begleitanzeige an, welche Typen für Ihre Anwendung verfügbar sind.

hinzufügen Sie einen Listener für das Ereignis `AdobePSDK.PSDKEventType.AD_STARTED`, das Folgendes ausführt:
1. Löscht vorhandene Anzeigen in der Bannerinstanz.
1. Ruft die Liste der begleitenden Anzeigen von `Ad.getCompanionAssets` ab.
1. Wenn die Liste der begleitenden Anzeigen nicht leer ist, müssen Sie die Liste für Bannerinstanzen durchlaufen.

   Jede Bannerinstanz (ein `AdBannerAsset`) enthält Informationen wie Breite, Höhe, Ressourcentyp (html, iframe oder statisch) und Daten, die zum Anzeigen des begleitenden Banners erforderlich sind.
1. Wenn bei einer Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.
1. Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Position anzeigt.

   Dies ist normalerweise ein `div` und Ihre Funktion verwendet das `div ID`, um das Banner anzuzeigen. Beispiel:

   hinzufügen Ereignis-Listener:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implementieren des Listener-Handlers:

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

