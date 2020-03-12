---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
seo-title: Benutzerdefinierte Tags abonnieren
title: Benutzerdefinierte Tags abonnieren
uuid: 43480265-4951-466a-a347-6debfb6935ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Benutzerdefinierte Tags abonnieren{#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren.
Um Tags zu abonnieren, weisen Sie der `subscribedTags` Eigenschaft einen Vektor zu, der die benutzerdefinierten Tag-Namen enthält. Wenn Sie auch die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags ändern müssen, weisen Sie der `adTags` Eigenschaft einen Vektor zu, der die benutzerdefinierten Tag-Namen der Anzeige enthält.

So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Legen Sie die benutzerdefinierten Tag-Namen global fest, indem Sie einen Vektor zuweisen, der die benutzerdefinierten Tags `subscribeTags` in enthält `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Beim Arbeiten mit HLS-Streams müssen Sie das `#` Präfix einschließen.

   Beispiel:

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Um die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags global zu ändern, weisen Sie der `adTags` Eigenschaft in einen Vektor zu, der die benutzerdefinierten Tag-Namen der Anzeige enthält, `PSDKConfig`.

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
   1. Erstellen Sie eine Medienplayer-Elementkonfiguration.

      >[!TIP]
      >
      >Am einfachsten ist es, eine standardmäßige Medienplayer-Elementkonfiguration zu erstellen.

   1. Weisen Sie einen Vektor zu, der die benutzerdefinierten Tags `subscribeTags` in enthält `MediaPlayerItemConfig`.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Um die vom standardmäßigen Opportunitätsgenerator im angegebenen Stream verwendeten Anzeigen-Tags zu ändern, weisen Sie der `adTags` Eigenschaft in `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Damit die Änderungen für den Stream wirksam werden, verwenden Sie beim Laden des Medienstreams die Elementkonfiguration des Medienplayers.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

