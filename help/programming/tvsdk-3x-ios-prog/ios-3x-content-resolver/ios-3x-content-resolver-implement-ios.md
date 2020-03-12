---
description: Sie können die Auflösungen auf Basis der Standardauflöser implementieren.
seo-description: Sie können die Auflösungen auf Basis der Standardauflöser implementieren.
seo-title: Implementieren eines benutzerdefinierten Angebots-/Inhaltsauflösers
title: Implementieren eines benutzerdefinierten Angebots-/Inhaltsauflösers
uuid: 0023f516-12f3-4548-93de-b0934789053b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Implementieren eines benutzerdefinierten Angebots-/Inhaltsauflösers {#implement-a-custom-opportunity-content-resolver}

Sie können die Auflösungen auf Basis der Standardauflöser implementieren.

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. Entwickeln Sie einen benutzerdefinierten Anzeigenauflöser, indem Sie die `PTContentResolver` abstrakte Klasse erweitern.

   `PTContentResolver` ist eine Schnittstelle, die von einer Content-Auflöser-Klasse implementiert werden muss. Eine abstrakte Klasse mit demselben Namen ist ebenfalls verfügbar und verarbeitet die Konfiguration automatisch (Abrufen des Delegaten).

   >[!TIP]
   >
   >`PTContentResolver` durch die `PTDefaultMediaPlayerClientFactory` Klasse offen gelegt wird. Kunden können einen neuen Content-Auflöser registrieren, indem sie die `PTContentResolver` abstrakte Klasse erweitern. Standardmäßig `PTDefaultAdContentResolver` wird ein Element in der Datei registriert, sofern es nicht ausdrücklich entfernt wurde `PTDefaultMediaPlayerClientFactory`.

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

1. Implementieren `shouldResolveOpportunity` und zurückgeben, `YES` wenn der Empfänger bearbeitet werden soll `PTPlacementOpportunity`.
1. Implementieren Sie, `resolvePlacementOpportunity`welche Beginn die alternativen Inhalte oder Anzeigen laden.
1. Nachdem die Anzeigen geladen wurden, bereiten Sie eine `PTTimeline` mit den Informationen über den einzufügenden Inhalt vor.

       Im Folgenden finden Sie einige nützliche Informationen zu Zeitschienen:
   
   * Es können mehrere `PTAdBreak`Typen von Pre-Roll-, Mid-Roll- und Post-Roll-Typen vorhanden sein.

      * A `PTAdBreak` hat Folgendes:

         * Eine `CMTimeRange` mit der Beginn- und Pausenzeit.

            Dies wird als range-Eigenschaft von festgelegt `PTAdBreak`.

         * `NSArray` von `PTAd`s.

            Dies wird als Ads-Eigenschaft festgelegt `PTAdBreak`.
   * Eine `PTAd` repräsentiert die Anzeige und jede `PTAd` hat folgende Eigenschaften:

      * Ein `PTAdHLSAsset` Satz als primäre Asset-Eigenschaft der Anzeige.
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
1. Registrieren Sie den benutzerdefinierten Inhalts-/Anzeigenauflöser durch Aufruf bei der standardmäßigen Medienplayer-Factory `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. Wenn Sie einen benutzerdefinierten Opportunitätsauflöser implementiert haben, registrieren Sie ihn bei der standardmäßigen Medienplayer-Factory.

   >[!TIP]
   >
   >Sie müssen keinen benutzerdefinierten Opportunitätsauflöser registrieren, um einen benutzerdefinierten Content-/Anzeigen-Auflöser zu registrieren.

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

Wenn der Player den Inhalt lädt und festgestellt wird, dass er vom Typ VOD oder LIVE ist, geschieht Folgendes:

* Wenn der Inhalt VOD ist, wird der benutzerdefinierte Inhaltsauflöser verwendet, um die Zeitleiste der Anzeige des gesamten Videos abzurufen.
* Wenn der Inhalt LIVE ist, wird der benutzerdefinierte Inhaltsauflöser jedes Mal aufgerufen, wenn eine Platzierungsmöglichkeit (Cue-Point) im Inhalt erkannt wird.