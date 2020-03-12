---
description: Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.
seo-description: Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.
seo-title: Untertitel verfügbar machen
title: Untertitel verfügbar machen
uuid: 1cd8761f-6e6f-4017-9852-fa61f36197c5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Untertitel verfügbar machen {#expose-subtitles}

Das TVSDK benachrichtigt Ihren Player-Client über die Verfügbarkeit der availableMediaCharacteristicsWithMediaSelectionOptions interner AVAsset-Benachrichtigungen, indem die PTMediaPlayerMediaSelectionOptionsAvailableNotification-Benachrichtigung verwendet wird.

Sie können auf die verfügbaren Untertitel über die der `PTMediaPlayerItem` Eigenschaft zugreifen `subtitlesOptions`.

So zeigen Sie Untertitel an:

1. Registrieren Sie den Client als Listener für die `PTMediaPlayerMediaSelectionOptionsAvailableNotification` Benachrichtigung.

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   Wenn Ihr Client diese Benachrichtigung erhält, sind die Untertitel im `PTMediaPlayerItem`Abschnitt bereit.
1. Implementieren Sie die `onMediaPlayerItemMediaSelectionOptionsAvailable` Methode ähnlich dem folgenden Beispiel:

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   Weitere Informationen zu alternativen Audiospuren finden Sie unter [Alternative Audiospuren](../../alternate-audio/ios-3x-alternate-audio.md).