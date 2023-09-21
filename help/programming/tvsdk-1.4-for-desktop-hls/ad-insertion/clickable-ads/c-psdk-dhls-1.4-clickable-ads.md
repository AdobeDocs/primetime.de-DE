---
description: TVSDK stellt Ihnen Informationen bereit, damit Sie auf Clickthrough-Anzeigen reagieren können. Bei der Erstellung Ihrer Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.
title: Klickbare Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Klickbare Anzeigen {#clickable-ads}

TVSDK stellt Ihnen Informationen bereit, damit Sie auf Clickthrough-Anzeigen reagieren können. Bei der Erstellung Ihrer Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.

Für TVSDK für Flash Runtime können nur lineare Anzeigen angeklickt werden.

## Antworten auf Klicks auf Anzeigen {#respond-to-clicks-on-ads}

Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, ist Ihre Anwendung für die Antwort verantwortlich. TVSDK liefert Informationen zur Ziel-URL.

In diesem Beispiel wird eine mögliche Methode zur Verwaltung von Anzeigenklicks gezeigt.

1. Zeigen Sie bei jeder Wiedergabe einer Anzeige eine Schaltfläche über dem Medienplayer an. Ein Benutzer, der auf die Anzeige klickt, wird zur Anzeigen-URL weitergeleitet. Diese Schaltfläche ist Teil der [!DNL ClickableAdsOverlay.xml].

   ```xml
      <?xml version="1.0"?> 
   <s:VGroup xmlns:fx="https://ns.adobe.com/mxml/2009"  
       xmlns:s="library://ns.adobe.com/flex/spark" percentWidth="100" horizontalAlign="center">     
           <fx:Declarations><fx:String id="text"/></fx:Declarations> 
           <s:Label text="{text}"  backgroundAlpha="0.75" backgroundColor="#DEDEDE"  
               color="#000000" paddingBottom="5" paddingRight="5" paddingLeft="5"  
               paddingTop="5"/> 
   </s:VGroup>
   ```

1. Fügen Sie diese Überlagerung in unser Beispiel für den Medienplayer ein. [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. Um die Ansicht nur sichtbar zu machen, wenn eine Anzeige wiedergegeben wird, achten Sie auf die `onAdStart` und `onAdComplete` -Ereignisse, die von gesendet werden.

   ```
   _player.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
   _player.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
   ```

   ```
      private function onAdStarted(event:AdPlaybackEvent):void { 
       var primaryAsset:AdAsset = event.ad.primaryAsset; 
       if (primaryAsset.adClick != null) { 
           clickableAdsOverlay.visible = true;  
       } 
   } 
   private function onAdCompleted(event:AdPlaybackEvent):void { 
       clickableAdsOverlay.visible = false; 
   }
   ```

1. Überwachen Sie Benutzerinteraktionen auf anklickbaren Anzeigen. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder klickt, benachrichtigen Sie TVSDK mit `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. Suchen Sie nach `AdclickEvent.AD_CLICK` -Ereignis.

   Wenn eine Anzeige wiedergegeben wird, sendet TVSDK die `AdClickEvent.AD_CLICK` -Ereignis, aus dem Sie die Clickthrough-URL und die zugehörigen Informationen abrufen können.

   ```
      _player.addEventListener(AdClickEvent.AD_CLICK, onAdClick);
   ```

1. Halten Sie den Medienplayer an, während Sie den Benutzer zur Anzeigen-URL weiterleiten.

   ```
   private function onAdClick(event:AdClickEvent):void { 
       _logger.info("#onAdClick Ad clicked. Target url is {0}", event.adClick.url);  
       _player.pause(); 
       var adRequest:URLRequest = new URLRequest(event.adClick.url); 
       navigateToURL(adRequest, event.adClick.title); 
   }
   ```

1. Zeigen Sie die Anzeigen-Clickthrough-URL und alle zugehörigen Informationen an.

       Sie können sie beispielsweise auf eine der folgenden Arten anzeigen:
   
   * Öffnen Sie die Clickthrough-URL in einem Browser in Ihrer Anwendung.

     Auf Desktop-Plattformen wird der Bereich für die Videoanzeige normalerweise zum Aufrufen von Clickthrough-URLs bei Benutzerklicks verwendet.
   * Leiten Sie den Benutzer zum externen mobilen Webbrowser um.

     Auf Mobilgeräten wird der Bereich für die Videoanzeige für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Daher wird dem Benutzer auf Mobilgeräten in der Regel eine separate Ansicht wie eine Sponsorschaltfläche als Möglichkeit zum Starten der Clickthrough-URL angezeigt.

1. Schließen Sie das Browser-Fenster, in dem die Clickthrough-Informationen angezeigt werden, und setzen Sie die Wiedergabe des Videos fort.
