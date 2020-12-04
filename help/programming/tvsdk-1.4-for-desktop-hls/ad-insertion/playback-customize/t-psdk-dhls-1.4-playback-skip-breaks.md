---
description: Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.
seo-description: Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.
seo-title: Werbeunterbrechungen für einen Zeitraum überspringen
title: Werbeunterbrechungen für einen Zeitraum überspringen
uuid: 1a18d5fd-c957-481b-83ae-2129590c1678
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Werbeunterbrechungen für einen Zeitraum überspringen{#skip-ad-breaks-for-a-period-of-time}

Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.

>[!IMPORTANT]
>
>Bei einer internen Suche, eine Anzeige zu überspringen, kann es zu einer leichten Pause bei der Wiedergabe kommen.

Im folgenden Beispiel einer benutzerdefinierten Anzeigenrichtlinienauswahl werden Anzeigen in den nächsten fünf Minuten (Pinnwandzeit) übersprungen, nachdem ein Benutzer eine Werbeunterbrechung gesehen hat.

1. Erweitern Sie die standardmäßige Anzeigenrichtlinien-Auswahl, um das Standardverhalten zu überschreiben.

   ```
   /** 
    * Custom ad policy selector. 
    */ 
   public class CustomAdPolicySelector extends DefaultAdPolicySelector { 
   
       /** 
        * Default constructor. 
        * 
        * @param item Associated media player item. 
        */ 
       public function CustomAdPolicySelector(item:MediaPlayerItem) { 
           super(item); 
   
           item.player.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED,  
                                        onAdBreakCompleted); 
       } 
   
       override public function selectPolicyForAdBreak(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForAdBreak(adPolicyInfo); 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       override public function selectAdBreaksToPlay(adPolicyInfo:AdPolicyInfo):Vector.<AdBreakTimelineItem> { 
           if (shouldPlayAds()) { 
               return super.selectAdBreaksToPlay(adPolicyInfo); 
           } 
   
           return new Vector.<AdBreakTimelineItem>(); 
       } 
   
       override public function selectPolicyForSeekIntoAd(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForSeekIntoAd(adPolicyInfo); 
           } 
   
           return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
       } 
   
       private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
           _lastAdBreakPlayedTime = new Date().valueOf(); 
       } 
   
       private function shouldPlayAds():Boolean { 
           var currentTime:Number = new Date().valueOf(); 
           return isNaN(_lastAdBreakPlayedTime) 
                   ||  (currentTime - _lastAdBreakPlayedTime > _minimumInterval); 
       } 
   
       private var _lastAdBreakPlayedTime:Number = NaN; 
       private var _minimumInterval:Number = 300000; // 5 minutes in milliseconds 
   }
   ```

1. Erstellen Sie eine neue Werbefabrik, die Ihre benutzerdefinierte Auswahl verwendet.

   ```
   public class CustomAdPolicyContentFactory extends DefaultContentFactory { 
   
       private var _adPolicySelector:CustomAdPolicySelector; 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomAdPolicyContentFactory() { 
   
       } 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
       if (!_adPolicySelector) { 
           _adPolicySelector = new CustomAdPolicySelector(item); 
       } 
   
       return _adPolicySelector; 
       } 
   }
   ```

1. Registrieren Sie die neue Factory-Klasse für Werbung, die mit dem MediaPlayer verwendet werden soll.

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

