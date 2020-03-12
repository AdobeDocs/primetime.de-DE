---
description: Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.
seo-description: Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.
seo-title: Werbeunterbrechungen für einen Zeitraum überspringen
title: Werbeunterbrechungen für einen Zeitraum überspringen
uuid: f8a5c1e3-e97f-421f-ac98-79de94a82955
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Werbeunterbrechungen für einen Zeitraum überspringen {#skip-ad-breaks-for-a-period-of-time}

Standardmäßig erzwingt TVSDK die Wiedergabe einer Werbeunterbrechung, wenn der Benutzer über eine Werbeunterbrechung sucht. Sie können das Verhalten anpassen, um einen Werbeunterbrechung zu überspringen, wenn der Zeitraum, der nach dem Abschluss eines vorherigen Umbruchs abgelaufen ist, innerhalb einer bestimmten Anzahl von Minuten liegt.

>[!IMPORTANT]
>
>Wenn Sie eine interne Suche abschließen müssen, um eine Anzeige zu vergeben, kann es während der Wiedergabe zu einer leichten Pause kommen.

Um das standardmäßige Verhalten von TVSDK-Werbeunterbrechungen zu überschreiben, können Sie die standardmäßige Anzeigenrichtlinien-Auswahl erweitern. Es stehen vier Werbeunterbrechungsrichtlinien zur Verfügung:

* PLAY
* SKIP

   >[!NOTE]
   >
   >Die SKIP-Werbeunterbrechungsrichtlinie funktioniert bei Live-Streams möglicherweise nicht wie erwartet, wenn eine Anzeige am Live-Point vorhanden ist. Bei einer Pre-Roll-Aktion führt SKIP beispielsweise zu einer Suche bis zum Ende der Werbeunterbrechung, die größer als der Live-Point sein könnte. In diesem Fall kann TVSDK eine Anzeige in der Mitte suchen.

* REMOVE_AFTER
* ENTFERNEN

   >[!NOTE]
   >
   >Die `REMOVE` Richtlinie für Werbeunterbrechungen wird für die Einstellung festgelegt. Adobe empfiehlt die Verwendung der `SKIP` Werbeunterbrechungsrichtlinie anstelle von `REMOVE`.

Im folgenden Beispiel einer benutzerdefinierten Anzeigenrichtlinienauswahl werden Anzeigen in den nächsten fünf Minuten (Pinnwandzeit) übersprungen, nachdem ein Benutzer eine Werbeunterbrechung gesehen hat.

1. Wenn der Benutzer eine Werbeunterbrechung abgeschlossen hat, speichern Sie die aktuelle Systemzeit.

   ```java
   @Override 
   public void onAdBreakComplete(AdBreak adBreak) { 
       ... 
       if (isShouldPlayUpcomingAdBreakRuleEnabled()) { 
           CustomAdPolicySelector.setLastAdBreakPlayedTime(System.currentTimeMillis()); 
           ... 
       } 
   }
   ```

1. Erweitern `AdPolicySelector`.

   ```java
   package com.adobe.mediacore.sample.advertising; 
   
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerItemConfig; 
   import com.adobe.mediacore.timeline.advertising.policy.*; 
   import com.adobe.mediacore.timeline.advertising.AdBreakTimelineItem; 
   import com.adobe.mediacore.metadata.AdvertisingMetadata; 
   
   import java.util.ArrayList; 
   import java.util.List; 
   
   public class CustomAdPolicySelector implements AdPolicySelector { 
   
       private static final long MIN_BREAK_INTERVAL = 300000; // 5 minutes for next ad break to be played 
       private MediaPlayerItem _mediaPlayerItem; 
       private static long _lastAdBreakPlayedTime; 
       private AdBreakWatchedPolicy watchedPolicy = AdBreakWatchedPolicy.WATCHED_ON_BEGIN; 
   
       public CustomAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           _mediaPlayerItem = mediaPlayerItem; 
           _lastAdBreakPlayedTime = 0; 
   
           if (mediaPlayerItem != null) { 
               watchedPolicy = extractWatchedPolicy(mediaPlayerItem.getConfig()); 
           } 
       } 
   
       @Override 
       public AdBreakPolicy selectPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
           if (shouldPlayAdBreaks() && adPolicyInfo.getAdBreakTimelineItems() != null) { 
   
               AdBreakTimelineItem item = adPolicyInfo.getAdBreakTimelineItems().get(0); 
   
               // This condition will remove the pre-roll ad from live stream after watching 
               if (item.getTime() == 0 && _mediaPlayerItem.isLive()) { 
                   return AdBreakPolicy.REMOVE_AFTER_PLAY; 
               } 
               if (item.getTime() == 0) { 
                   return AdBreakPolicy.PLAY; 
               } 
   
               // This condition will remove every ad break that has been watched once.  
               // Comment this section if you want to play watched ad breaks again. 
               if (item.isWatched()) { 
                   return AdBreakPolicy.SKIP; 
               } 
   
               return AdBreakPolicy.REMOVE_AFTER_PLAY; 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       @Override 
       public List<AdBreakTimelineItem> selectAdBreaksToPlay(AdPolicyInfo adPolicyInfo) { 
   
           if (shouldPlayAdBreaks()) { 
   
               List<AdBreakTimelineItem> timelineItems = adPolicyInfo.getAdBreakTimelineItems(); 
               AdBreakTimelineItem item; 
               List<AdBreakTimelineItem> selectedItems = new ArrayList<AdBreakTimelineItem>(); 
   
               if (timelineItems != null && timelineItems.size() > 0) { 
   
                   // Seek Forward Condition 
                   if (adPolicyInfo.getCurrentTime() <= adPolicyInfo.getSeekToTime()) { 
                       item = timelineItems.get(0); 
   
                       // Resume logic - This will be helpful in resuming the content  
                       // from last saved playback session, and just play the pre-roll ad 
                       if(adPolicyInfo.getCurrentTime() == 0) { 
                           if(item.getTime() == 0 && !item.isWatched()) { 
                               // comment this line if you just need to seek to the user's  
                               // last known position without playing pre-roll ad. ZD#820 
                               selectedItems.add(item); 
                               return selectedItems; 
                           } 
                           else{ 
                               return null; 
                           } 
                       } else { 
                           item = timelineItems.get(timelineItems.size()-1); 
                           if (!item.isWatched()) { 
                               selectedItems.add(item); 
                               return selectedItems; 
                           } 
                       } 
   
                       // Seek backward condition 
                   } else if (adPolicyInfo.getCurrentTime() > adPolicyInfo.getSeekToTime()) { 
                       item = timelineItems.get(0); 
   
                       if(!item.isWatched()) { 
                           selectedItems.add(item); 
                           return selectedItems; 
                       } else { 
                           return null; 
                       } 
                   } 
               } 
           } 
           return null; 
       } 
   
       @Override 
       public AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo) { 
           // Simple Ad Policy selector 
           // if the first ad in the break was watched,  
           // skip to the next add after the seek position 
           // otherwise, play the ads in the break from the beginning 
   
           List<AdBreakTimelineItem> timelineItems = adPolicyInfo.getAdBreakTimelineItems(); 
           if (timelineItems != null && timelineItems.size() > 0) { 
               if (timelineItems.get(0).isWatched()) { 
                   return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
               } 
           } 
   
           // Resume play from the next ad in the break 
           return AdPolicy.PLAY_FROM_AD_BREAK_BEGIN; 
   
       } 
   
       @Override 
       public AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
           return watchedPolicy; 
       } 
   
       public static void setLastAdBreakPlayedTime(long lastAdBreakPlayedTime) { 
           _lastAdBreakPlayedTime = lastAdBreakPlayedTime; 
       } 
   
       private boolean shouldPlayAdBreaks() { 
           long currentTime = System.currentTimeMillis(); 
   
           if (_lastAdBreakPlayedTime <= 0) { 
               return true; 
           } 
   
           if (_lastAdBreakPlayedTime > 0 &&  
             (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) { 
               return true; 
           } 
   
           // return false for not playing Ad if this  
           // Ad occurs with 5 minutes of last Ad playback 
           return false; 
       } 
   
       private AdBreakWatchedPolicy extractWatchedPolicy(MediaPlayerItemConfig config) { 
           if (config != null) { 
               AdvertisingMetadata metadata = config.getAdvertisingMetadata(); 
               if (metadata != null) { 
                   return metadata.getAdBreakWatchedPolicy(); 
               } 
           } 
           return AdBreakWatchedPolicy.WATCHED_ON_BEGIN; 
       } 
   } 
   ```

