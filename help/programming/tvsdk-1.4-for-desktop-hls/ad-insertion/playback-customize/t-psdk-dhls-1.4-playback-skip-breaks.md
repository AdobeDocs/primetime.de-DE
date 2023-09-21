---
description: Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer die Suche über eine Werbeunterbrechung durchführt. Sie können das Verhalten so anpassen, dass eine Werbeunterbrechung übersprungen wird, wenn die seit dem Abschluss einer vorherigen Werbeunterbrechung verstrichene Zeit innerhalb einer bestimmten Anzahl von Minuten liegt.
title: Werbeunterbrechungen für einen bestimmten Zeitraum überspringen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Werbeunterbrechungen für einen bestimmten Zeitraum überspringen{#skip-ad-breaks-for-a-period-of-time}

Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer die Suche über eine Werbeunterbrechung durchführt. Sie können das Verhalten so anpassen, dass eine Werbeunterbrechung übersprungen wird, wenn die seit dem Abschluss einer vorherigen Werbeunterbrechung verstrichene Zeit innerhalb einer bestimmten Anzahl von Minuten liegt.

>[!IMPORTANT]
>
>Wenn eine interne Suche besteht, um eine Anzeige zu überspringen, kann es bei der Wiedergabe zu einer leichten Pause kommen.

Im folgenden Beispiel einer benutzerdefinierten Anzeigenrichtlinienauswahl werden Anzeigen in den nächsten fünf Minuten (Uhrzeit) übersprungen, nachdem ein Benutzer eine Werbeunterbrechung gesehen hat.

1. Erweitern Sie die standardmäßige Anzeigenrichtlinienauswahl, um das Standardverhalten zu überschreiben.

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

1. Erstellen Sie eine neue Werbe-Factory, die Ihren benutzerdefinierten Selektor verwendet.

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

1. Registrieren Sie die neue Werbe-Factory-Klasse, die mit dem MediaPlayer verwendet werden soll.

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
