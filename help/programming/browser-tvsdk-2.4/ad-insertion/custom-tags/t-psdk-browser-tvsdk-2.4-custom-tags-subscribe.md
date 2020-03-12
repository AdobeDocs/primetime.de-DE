---
description: Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der MPD-Datei (Media Presentation Description) gefunden werden.
seo-description: Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der MPD-Datei (Media Presentation Description) gefunden werden.
seo-title: Benutzerdefinierte Anzeigen-Tags abonnieren
title: Benutzerdefinierte Anzeigen-Tags abonnieren
uuid: 208f61f4-dc33-4363-aa71-878458740a8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Benutzerdefinierte Anzeigen-Tags abonnieren{#subscribe-to-custom-ad-tags}

Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der MPD-Datei (Media Presentation Description) gefunden werden.

Sie müssen die Tags abonnieren, bevor Sie Beginn wiedergeben können.
Um Tags zu abonnieren, legen Sie einen Vektor mit den benutzerdefinierten Tag-Namen für die `subscribedTags` Eigenschaft fest. Wenn Sie auch die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags ändern müssen, stellen Sie einen Vektor mit den benutzerdefinierten Tag-Namen der Anzeige auf die `adTags` Eigenschaft ein.

So abonnieren Sie benutzerdefinierte Tags:

1. Erstellen Sie eine neue Elementkonfiguration für den Medienplayer.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Erstellen Sie einen leeren String-Vektor.

   ```js
   var subscribeTags = [];
   ```

1. Hinzufügen die benutzerdefinierten Tag-Namen diesem Vektor.

   >[!IMPORTANT]
   >
   >Wenn Sie mit HLS-Streams zu tun haben, denken Sie daran, das `#` Präfix einzuschließen.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Weisen Sie den aktualisierten Vektor der `mediaPlayerItemConfig.subscribeTags` Eigenschaft zu.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Erstellen Sie einen leeren String-Vektor.

   ```js
   var adTags= [];
   ```

1. Hinzufügen Sie den benutzerdefinierten Tag-Namen für die Anzeige diesem Vektor an.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Weisen Sie den aktualisierten Vektor der `mediaPlayerItemConfig.adTags` Eigenschaft zu.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Verwenden Sie beim Laden des Medienstreams die Medienplayer-Elementkonfiguration.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

