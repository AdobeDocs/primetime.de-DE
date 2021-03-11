---
description: TVSDK stellt Informationen bereit, damit Sie Clickthrough-Anzeigen bearbeiten können. Beim Erstellen der Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.
title: Klickbare Anzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Klickbare Anzeigen {#clickable-ads}

TVSDK stellt Informationen bereit, damit Sie Clickthrough-Anzeigen bearbeiten können. Beim Erstellen der Player-Benutzeroberfläche müssen Sie entscheiden, wie Sie reagieren, wenn ein Benutzer auf eine anklickbare Anzeige klickt.

Für TVSDK für Flash Runtime können nur lineare Anzeigen angeklickt werden.

## Antworten Sie auf Klicks auf Anzeigen {#respond-to-clicks-on-ads}

Wenn ein Benutzer auf eine Anzeige oder eine zugehörige Schaltfläche klickt, ist Ihre Anwendung für die Beantwortung verantwortlich. TVSDK liefert Informationen zur Ziel-URL.

Dieses Beispiel zeigt eine Möglichkeit, Anzeigenklicks zu verwalten.

1. Bei jeder Wiedergabe einer Anzeige wird eine Schaltfläche über dem Medienplayer angezeigt. Ein Benutzer, der auf die Anzeige klickt, wird zur Anzeigen-URL umgeleitet. Diese Schaltfläche ist Teil von [!DNL ClickableAdsOverlay.xml].

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

1. Schließen Sie diese Überlagerung in unser Medienplayer-Beispiel ein, [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. Um die Ansicht nur bei der Wiedergabe einer Anzeige sichtbar zu machen, suchen Sie nach den von ausgelösten Ereignissen `onAdStart` und `onAdComplete`.

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

1. Überwachen Sie Benutzerinteraktionen auf klickbaren Anzeigen. Wenn der Benutzer die Anzeige oder Schaltfläche berührt oder klickt, benachrichtigen Sie TVSDK mit `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. Suchen Sie nach dem Ereignis `AdclickEvent.AD_CLICK`.

   Bei der Wiedergabe einer Anzeige löst TVSDK das `AdClickEvent.AD_CLICK`-Ereignis aus, aus dem Sie die Clickthrough-URL und zugehörige Informationen abrufen können.

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

      Auf Desktop-Plattformen wird der Videoanzeigenwiedergabebereich in der Regel zum Aufrufen von Clickthrough-URLs beim Klicken auf den Benutzer verwendet.
   * Leitet den Benutzer zum externen mobilen Webbrowser um.

      Auf Mobilgeräten wird der Bereich für Video- und Wiedergabe für andere Funktionen verwendet, z. B. zum Ausblenden und Anzeigen von Steuerelementen, zum Anhalten der Wiedergabe, zum Erweitern auf den Vollbildmodus usw. Daher wird dem Benutzer auf Mobilgeräten in der Regel eine separate Ansicht, z. B. eine Sponsorschaltfläche, angezeigt, um die Clickthrough-URL zu starten.

1. Schließen Sie das Browserfenster, in dem die Clickthrough-Informationen angezeigt werden, und nehmen Sie die Wiedergabe des Videos wieder auf.
