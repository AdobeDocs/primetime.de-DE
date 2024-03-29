---
description: Sie können ein TV-ähnliches Erlebnis aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können.
title: Teilweise Einfügen einer Werbeunterbrechung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Teilweise Einfügen einer Werbeunterbrechung {#partial-ad-break-insertion}

Sie können ein TV-ähnliches Erlebnis aktivieren, um mitten in einer Anzeige in Live-Streams mitmachen zu können.

Mit der Funktion &quot;Teilweise Werbeunterbrechung&quot;können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb eines Midroll startet, dieser in diesem Midroll beginnt. Es ähnelt dem Wechsel zu einem Fernsehkanal und die Werbung läuft nahtlos.

Wenn ein Benutzer beispielsweise mitten in einer 90-Sekunden-Werbeunterbrechung (drei 30-Sekunden-Anzeigen) und 10 Sekunden nach der zweiten Anzeige (d. h. nach 40 Sekunden Werbeunterbrechung) Mitglied wird, passiert Folgendes:

* Die zweite Anzeige wird für die verbleibende Dauer (20 Sek.) gefolgt von der dritten Anzeige wiedergegeben.
* Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Nur der Tracker für die dritte Anzeige wird ausgelöst.

Dieses Verhalten ist standardmäßig nicht aktiviert. Gehen Sie wie folgt vor, um diese Funktion in Ihrer App zu aktivieren.

1. Deaktivieren Sie die Live-Vorwahlen mithilfe der Methode setEnableLivePreroll der AdvertisingMetadata-Klasse.

   ```
   advertisingMetadata.setEnableLivePreroll(String.valueOf(false))
   ```

1. Schalten Sie die Voreinstellung für &quot;Teil-Werbeunterbrechung einfügen&quot;ein. Verwenden Sie die neue Methode setPartialAdBreakPref in der MediaPlayer-Oberfläche, um diese Funktion EIN zu schalten. Verwenden Sie die Methode getPartialAdBreakPref , um den aktuellen Status dieser Voreinstellung zu ermitteln.

   ```
   MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
   
          mediaPlayer.setPartialAdBreakPref(true); 
   ```

1. Für diese Funktion müssen Sie eine benutzerdefinierte Auswahl für Anzeigenrichtlinien implementieren, um das Verhalten anzupassen. Wenn Sie noch keine benutzerdefinierte Implementierung der AdvertisingFactory-Klasse haben, fügen Sie eine neue AdvertisingFactory-Implementierung hinzu. Überschreiben Sie die Methode createAdPolicySelector . Diese Methode gibt eine neue Instanz der Implementierung von AdPolicySelector zurück.

   Nachfolgend finden Sie eine Beispielimplementierung als Referenz. Die folgende Beispielimplementierung ist im com.adobe.mediacore -Paket verfügbar. Es ist jedoch vereinfacht, um eine einfache Referenz zu erhalten, und es wird nicht empfohlen, unverändert zu verwenden.

   1. Auswahl von Beispielanzeigenrichtlinien

      ```
       package com.adobe.mediacore;
      
      import com.adobe.mediacore.logging.Log; 
      import com.adobe.mediacore.logging.Logger; 
      import com.adobe.mediacore.metadata.*; 
      import com.adobe.mediacore.timeline.advertising.*; 
      
      import java.util.ArrayList; 
      import java.util.List; 
      
      public class PartialAdBreakAdPolicySelector implements AdPolicySelector { 
          private static final String LOG_TAG = "[PSDK]::" + DefaultAdPolicySelector.class.getSimpleName(); 
          private final Logger _logger = Log.getLogger(LOG_TAG); 
      
          private final MediaPlayerItem _mediaPlayerItem; 
          private final AdBreakAsWatched _adBreakAsWatchedPolicy; 
      
          public PartialAdBreakAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
              _mediaPlayerItem = mediaPlayerItem; 
              _adBreakAsWatchedPolicy = extractAdBreakAsWatchedPolicy(_mediaPlayerItem); 
          } 
      
          @Override 
          public AdBreakPolicy selectPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              if (adPolicyInfo.getAdBreakPlacements().size() > 0) { 
                  AdBreakPlacement adBreakTimelineItem = adPolicyInfo.getAdBreakPlacements().get(0); 
                  if (adPolicyInfo.getMode() == AdPolicyMode.SEEK && adBreakTimelineItem.getAdBreak().isWatched()) { 
                      return AdBreakPolicy.SKIP; 
                  } 
              } 
      
              AdSignalingMode adSignalingMode = AdSignalingMode.DEFAULT; 
              if (_mediaPlayerItem != null) { 
                  MetadataNode metadata = (MetadataNode) _mediaPlayerItem.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adSignalingMode = advertisingMetadata.getSignalingMode(); 
                      } 
                  } 
              } 
      
              // can't remove main content due to a ave bug, need to check if stream is live or ad signaling mode is manifest cue 
              if (_mediaPlayerItem.isLive() || adSignalingMode == AdSignalingMode.MANIFEST_CUES) { 
                  return AdBreakPolicy.PLAY; 
              } 
      
              return AdBreakPolicy.REMOVE_AFTER_PLAY; 
          } 
      
          @Override 
          public List<AdBreakPlacement> selectAdBreaksToPlay(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectAdBreaksToPlay", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              List<AdBreakPlacement> adBreakPlacements = adPolicyInfo.getAdBreakPlacements(); 
              if (adBreakPlacements != null) { 
                  int size = adBreakPlacements.size(); 
                  List<AdBreakPlacement> adBreaks = new ArrayList<AdBreakPlacement>(); 
                  if (size > 0 && adPolicyInfo.getCurrentTime() <= adPolicyInfo.getSeekToTime()) { 
                      AdBreakPlacement adBreak = adBreakPlacements.get(size - 1); 
                      if (!adBreak.getAdBreak().isWatched()) { 
                          adBreaks.add(adBreak); 
                          return adBreaks; 
                      } 
                  } 
              } 
      
              return null; 
          } 
      
          @Override 
          public AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForSeekIntoAd", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              // If you really want to allow seek during ads (you likely do not). 
              return AdPolicy.PLAY; 
          } 
      
          @Override 
          public AdBreakAsWatched selectWatchedPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectWatchedPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              return _adBreakAsWatchedPolicy; 
          } 
      
          /** 
           * Extract the ad break watched policy for the specified media player item. 
           * 
           * @param item Associated media player item. 
           * @return a valid ad break watched policy. 
           */ 
          private AdBreakAsWatched extractAdBreakAsWatchedPolicy(MediaPlayerItem item) { 
              AdBreakAsWatched adBreakWatchedPolicy = AdBreakAsWatched.AD_BREAK_AS_WATCHED_ON_BEGIN; 
      
              if (item != null) { 
                  MetadataNode metadata = (MetadataNode) item.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adBreakWatchedPolicy = advertisingMetadata.getAdBreakAsWatched(); 
                      } 
                  } 
              } 
      
              return adBreakWatchedPolicy; 
          } 
      } 
      ```

   1. Beispiel-Werbewerkstatt

      ```
      private AdvertisingFactory createPartialAdBreakFactory() { 
      return new AdvertisingFactory() { 
      @Override 
                   public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
                      return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
                   } 
      
      // Rest of the interface methods can be overridden as per your  
      // customization needs 
      // As shown next 
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
        } 
      // . . . 
      
       } 
      } 
      ```

   1. Registrieren Sie unsere AdvertisingFactory beim Medienplayer.

      ```
      AdvertisingFactory advertisingFactory = createPartialAdBreakFactory();  
      
      if (advertisingFactory != null) { 
                  mediaPlayer.registerAdClientFactory(advertisingFactory); 
      } 
      ```

   1. createAdPolicySelector -Methode überschreiben

      ```
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
      } 
      ```
