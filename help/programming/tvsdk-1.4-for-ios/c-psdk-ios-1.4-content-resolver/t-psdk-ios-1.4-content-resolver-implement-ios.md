---
description: Sie können Ihre Resolver auf der Basis der Standard-Resolver implementieren.
title: Implementieren eines benutzerdefinierten Opportunities/Content Resolvers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Opportunities/Content Resolvers{#implement-a-custom-opportunity-content-resolver}

Sie können Ihre Resolver auf der Basis der Standard-Resolver implementieren.

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. Entwickeln Sie einen benutzerdefinierten Anzeigenauflöser, indem Sie die `PTContentResolver` abstrakte Klasse.

   `PTContentResolver` ist eine Schnittstelle, die von einer Content Resolver-Klasse implementiert werden muss. Eine abstrakte Klasse mit demselben Namen ist ebenfalls verfügbar und verarbeitet die Konfiguration automatisch (Abrufen des Delegats).

   >[!TIP]
   >
   >`PTContentResolver` über die `PTDefaultMediaPlayerClientFactory` -Klasse. Clients können einen neuen Inhaltsauflöser registrieren, indem sie die `PTContentResolver` abstrakte Klasse. Standardmäßig und sofern nicht ausdrücklich entfernt, wird ein `PTDefaultAdContentResolver` im `PTDefaultMediaPlayerClientFactory`.

   ```
   @protocol PTContentResolver <NSObject> 
   @required 
   + (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity;  
   //Detector returns YES/NO if it should handle the following placement opportunity 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                 delegate:(id<PTContentResolverDelegate> delegate); 
   - (void)process:(PTPlacementOpportunity *)opportunity; 
   - (void)timeout:(PTPlacementOpportunity *)opportunity;  
   //The timeout method gets invoked if the TVSDK decides that the  
   //PTContentResolver is taking too much time to respond. 
   @end 
   
   @interface PTContentResolver : NSObject <PTContentResolver> 
   
   @property (readonly) id<PTContentResolverDelegate> delegate; 
   @property (readonly) PTMediaPlayerItem *playerItem; 
   
   - (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity; 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                  delegate:(id<PTContentResolverDelegate>) delegate; 
   - (void)process:(NSArray *)opportunities; 
   - (void)cancel:(NSArray *)opportunities; 
   @end
   ```

1. Implementierung `shouldResolveOpportunity` und zurück `YES` ob sie die empfangenen `PTPlacementOpportunity`.
1. Implementierung `resolvePlacementOpportunity`, wodurch das Laden der alternativen Inhalte oder Anzeigen beginnt.
1. Nachdem die Anzeigen geladen wurden, bereiten Sie eine `PTTimeline` mit den Informationen zum einzufügenden Inhalt.

       Im Folgenden finden Sie einige nützliche Informationen zu Zeitleisten:
   
   * Es kann mehrere `PTAdBreak`s der Typen &quot;Pre-Roll&quot;, &quot;Mid-Roll&quot;und &quot;Post-Roll&quot;.

      * A `PTAdBreak` hat Folgendes:

         * A `CMTimeRange` mit der Startzeit und Dauer der Pause.

           Dies wird als Bereichseigenschaft von `PTAdBreak`.

         * `NSArray` von `PTAd`s.

           Dies wird als Ads-Eigenschaft von `PTAdBreak`.

   * A `PTAd` stellt die Anzeige dar und jeder `PTAd` hat Folgendes:

      * A `PTAdHLSAsset` als primäre Asset-Eigenschaft der Anzeige festlegen.
      * Möglicherweise mehrere `PTAdAsset` Instanzen als anklickbare Anzeigen oder Banneranzeigen.

   Beispiel:

   ```
   NSMutableArray *ptBreaks = [[[NSMutableArray alloc] init] autorelease]; 
   
   // Prepare the primary asset of the ad - links to ad m3u8 
   PTAdHLSAsset *ptAdAsset = [[[PTAdHLSAsset alloc] init] autorelease]; 
   ptAdAsset.source = AD_SOURCE_M3U8; 
   ptAdAsset.id = FAKE_NUMBER_ID; 
   ptAdAsset.format = @"video"; 
   
   // Prepare the ad itself. 
   PTAd *ptAd = [[[PTAd alloc] init] autorelease]; 
   ptAd.primaryAsset = ptAdAsset; 
   ptAd.primaryAsset.ad = ptAd; 
   
   // Prepare the break and add the ad created above. 
   PTAdBreak *ptBreak = [[[PTAdBreak alloc] init] autorelease]; 
   ptBreak.relativeRange = CMTimeRangeMake(BREAK_START_TIME, BREAK_DURATION_VALUE); 
   [ptBreak addAd:ptAd]; 
   
   // Add the break to array of breaks. 
   [ptBreaks addObject:adBreak]; 
   
   // Once all breaks have been prepared, they can be set on timeline 
   PTTimeline *_timeline = [[PTTimeline alloc] init]; 
   _timeline.adBreaks = ptBreaks;
   ```

1. Aufruf `didFinishResolvingPlacementOpportunity`, der die `PTTimeline`.
1. Registrieren Sie Ihre benutzerdefinierten Inhalte/Anzeigenauflöser bei der standardmäßigen Medienplayer-Factory, indem Sie `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. Wenn Sie einen benutzerdefinierten Opportunities Resolver implementiert haben, registrieren Sie ihn bei der standardmäßigen Medienplayer-Factory.

   >[!TIP]
   >
   >Sie müssen keinen benutzerdefinierten Opportunity-Resolver registrieren, um einen benutzerdefinierten Content/Anzeigen-Resolver zu registrieren.

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

Wenn der Player den Inhalt lädt und als VOD- oder LIVE-Typ ermittelt wird, geschieht eine der folgenden Aktionen: >
* Wenn der Inhalt VOD ist, wird der benutzerdefinierte Content Resolver verwendet, um die Anzeigen-Timeline des gesamten Videos abzurufen.
* Wenn der Inhalt LIVE ist, wird der Resolver für benutzerspezifischen Inhalt jedes Mal aufgerufen, wenn eine Platzierungsmöglichkeit (Cue-Punkt) im Inhalt erkannt wird.
