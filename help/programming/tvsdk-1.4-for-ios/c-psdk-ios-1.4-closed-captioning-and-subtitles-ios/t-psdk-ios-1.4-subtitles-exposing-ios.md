---
description: Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der verfügbaren verfügbaren verfügbaren verfügbaren verfügbaren verfügbaren Variablen des internen AVAssets "availableMediaCharacteristicsWithMediaSelectionOptions", indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification verwendet wird.
title: Untertitel verfügbar machen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Untertitel verfügbar machen {#expose-subtitles}

Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der verfügbaren verfügbaren verfügbaren verfügbaren verfügbaren verfügbaren Variablen des internen AVAssets &quot;availableMediaCharacteristicsWithMediaSelectionOptions&quot;, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification verwendet wird.

Sie können auf die verfügbaren Untertitel über die `PTMediaPlayerItem` -Eigenschaft `subtitlesOptions`.

So zeigen Sie Untertitel an:

1. Registrieren Sie den Client als Listener für die `PTMediaPlayerMediaSelectionOptionsAvailableNotification` Benachrichtigung.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wenn Ihr Client diese Benachrichtigung erhält, sind die Untertitel im `PTMediaPlayerItem`.
1. Implementieren des `onMediaPlayerItemMediaSelectionOptionsAvailable` -Methode ähnlich dem folgenden Beispiel:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Weitere Informationen zu alternativen Audiospuren finden Sie unter  [Alternatives Audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).
