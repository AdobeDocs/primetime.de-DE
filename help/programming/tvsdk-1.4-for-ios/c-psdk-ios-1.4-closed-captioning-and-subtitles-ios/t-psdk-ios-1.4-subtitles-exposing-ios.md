---
description: Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.
seo-description: Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.
seo-title: Untertitel verfügbar machen
title: Untertitel verfügbar machen
uuid: 657ab9c7-b205-4d13-81a7-51bc8e7d5ee2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Untertitel {#expose-subtitles} verfügbar machen

Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.

Sie können auf die verfügbaren Untertitel über die Eigenschaft `PTMediaPlayerItem` `subtitlesOptions` zugreifen.

So zeigen Sie Untertitel an:

1. Registrieren Sie den Client als Listener für die `PTMediaPlayerMediaSelectionOptionsAvailableNotification`-Benachrichtigung.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wenn Ihr Client diese Benachrichtigung erhält, sind die Untertitel in `PTMediaPlayerItem` bereit.
1. Implementieren Sie die `onMediaPlayerItemMediaSelectionOptionsAvailable`-Methode ähnlich dem folgenden Beispiel:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Weitere Informationen zu alternativen Audiospuren finden Sie unter [Alternatives Audio](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).