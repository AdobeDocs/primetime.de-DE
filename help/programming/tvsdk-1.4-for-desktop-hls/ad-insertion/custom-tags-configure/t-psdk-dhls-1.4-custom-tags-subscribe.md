---
description: TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.
title: Benutzerdefinierte Tags abonnieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Benutzerdefinierte Tags abonnieren{#subscribe-to-custom-tags}

TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte im Inhaltsmanifest gefunden werden.

Vor den Wiedergabe-Beginn müssen Sie die Tags abonnieren.
Um Tags zu abonnieren, weisen Sie der Eigenschaft `subscribedTags` einen Vektor zu, der die benutzerdefinierten Tag-Namen enthält. Wenn Sie auch die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags ändern müssen, weisen Sie der Eigenschaft `adTags` einen Vektor zu, der die benutzerdefinierten Tag-Namen der Anzeige enthält.

So werden Sie über benutzerdefinierte Tags in HLS-Manifesten benachrichtigt:

1. Stellen Sie die benutzerdefinierten Tag-Namen global ein, indem Sie einen Vektor mit den benutzerdefinierten Tags `subscribeTags` in `MediaPlayerItemConfig` zuweisen.

   >[!IMPORTANT]
   >
   >Sie müssen beim Arbeiten mit HLS-Streams das Präfix `#` einschließen.

   Beispiel:

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Um die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags global zu ändern, weisen Sie der Eigenschaft `adTags` in `PSDKConfig` einen Vektor zu, der die benutzerdefinierten Tag-Namen der Anzeige enthält.

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

   1. Weisen Sie `subscribeTags` in `MediaPlayerItemConfig` einen Vektor zu, der die benutzerdefinierten Tags enthält.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Um die vom standardmäßigen Opportunitätsgenerator im angegebenen Stream verwendeten Anzeigen-Tags zu ändern, weisen Sie der `adTags`-Eigenschaft in `mediaPlayerItemConfig` einen Vektor zu, der die benutzerdefinierten Tag-Namen enthält

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Damit die Änderungen für den Stream wirksam werden, verwenden Sie beim Laden des Medienstreams die Elementkonfiguration des Medienplayers.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

