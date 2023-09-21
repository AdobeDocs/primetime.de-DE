---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
title: Benutzerdefinierte Tags abonnieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Benutzerdefinierte Tags abonnieren{#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor dem Start der Wiedergabe müssen Sie die Tags abonnieren.
Um Tags zu abonnieren, weisen Sie der `subscribedTags` -Eigenschaft. Wenn Sie auch die Anzeigen-Tags ändern müssen, die vom standardmäßigen Opportunity Generator verwendet werden, weisen Sie dem `adTags` -Eigenschaft.

So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Globales Festlegen der benutzerdefinierten Anzeigen-Tag-Namen durch Zuweisen eines Vektors, der die benutzerdefinierten Tags enthält zu `subscribeTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Sie müssen die `#` Präfix beim Arbeiten mit HLS-Streams.

   Beispiel:

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Um die Anzeigen-Tags, die vom standardmäßigen Opportunity Generator verwendet werden, global zu ändern, weisen Sie dem `adTags` -Eigenschaft in `PSDKConfig`.

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. Damit alle globalen Einstellungen wirksam werden, ersetzen Sie die aktuelle Ressource.

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. So legen Sie bei Bedarf die abonnierten Tag-Namen für einen Stream fest:
   1. Erstellen Sie eine Elementkonfiguration für den Medienplayer.

      >[!TIP]
      >
      >Am einfachsten ist es, eine standardmäßige Medienplayer-Elementkonfiguration zu erstellen.

   1. Weisen Sie einen Vektor zu, der die benutzerdefinierten Tags enthält zu `subscribeTags` in `MediaPlayerItemConfig`.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Um die Anzeigen-Tags zu ändern, die vom standardmäßigen Opportunity-Generator im angegebenen Stream verwendet werden, weisen Sie dem `adTags` -Eigenschaft in `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Damit die Änderungen für den Stream wirksam werden, verwenden Sie beim Laden des Medien-Streams die Elementkonfiguration des Medienplayers.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
