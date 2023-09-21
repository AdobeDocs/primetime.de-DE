---
description: Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der Datei "Media Presentation Description"(MPD) gefunden werden.
title: Abonnieren von benutzerdefinierten Anzeigen-Tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Abonnieren von benutzerdefinierten Anzeigen-Tags{#subscribe-to-custom-ad-tags}

Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der Datei &quot;Media Presentation Description&quot;(MPD) gefunden werden.

Sie müssen die Tags abonnieren, bevor die Wiedergabe gestartet wird.
Um Tags zu abonnieren, setzen Sie einen Vektor, der die benutzerdefinierten Tag-Namen enthält, auf die `subscribedTags` -Eigenschaft. Wenn Sie auch die Anzeigen-Tags ändern müssen, die vom standardmäßigen Opportunity Generator verwendet werden, setzen Sie einen Vektor, der die benutzerdefinierten Anzeigen-Tag-Namen enthält, auf `adTags` -Eigenschaft.

So abonnieren Sie benutzerdefinierte Tags:

1. Erstellen Sie eine neue Elementkonfiguration für den Medienplayer.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Erstellen Sie einen leeren Zeichenfolgenvektor.

   ```js
   var subscribeTags = [];
   ```

1. Fügen Sie diesem Vektor die benutzerdefinierten Tag-Namen hinzu.

   >[!IMPORTANT]
   >
   >Wenn Sie mit HLS-Streams arbeiten, denken Sie daran, die `#` -Präfix.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Weisen Sie den aktualisierten Vektor dem `mediaPlayerItemConfig.subscribeTags` -Eigenschaft.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Erstellen Sie einen leeren Zeichenfolgenvektor.

   ```js
   var adTags= [];
   ```

1. Fügen Sie diesem Vektor den benutzerdefinierten Anzeigen-Tag-Namen hinzu.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Weisen Sie den aktualisierten Vektor dem `mediaPlayerItemConfig.adTags` -Eigenschaft.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Verwenden Sie beim Laden des Medien-Streams die Elementkonfiguration des Medienplayers.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```
