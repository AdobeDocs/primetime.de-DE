---
description: Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der MPD-Datei (Media Presentation Description) gefunden werden.
title: Benutzerdefinierte Anzeigen-Tags abonnieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Benutzerdefinierte Anzeigen-Tags abonnieren{#subscribe-to-custom-ad-tags}

Browser TVSDK bereitet TimedMetadata-Objekte für abonnierte Tags vor, sobald diese Objekte in der MPD-Datei (Media Presentation Description) gefunden werden.

Sie müssen die Tags abonnieren, bevor Sie Beginn wiedergeben können.
Um Tags zu abonnieren, legen Sie für einen Vektor, der die benutzerdefinierten Tag-Namen enthält, die Eigenschaft `subscribedTags` fest. Wenn Sie auch die vom standardmäßigen Opportunitätsgenerator verwendeten Anzeigen-Tags ändern müssen, stellen Sie einen Vektor mit den benutzerdefinierten Tag-Namen der Anzeige auf die Eigenschaft `adTags` ein.

So abonnieren Sie benutzerdefinierte Tags:

1. Erstellen Sie eine neue Elementkonfiguration für den Medienplayer.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Erstellen Sie einen leeren String-Vektor.

   ```js
   var subscribeTags = [];
   ```

1. hinzufügen die benutzerdefinierten Tag-Namen diesem Vektor.

   >[!IMPORTANT]
   >
   >Wenn Sie mit HLS-Streams zu tun haben, denken Sie daran, das Präfix `#` einzuschließen.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Weisen Sie den aktualisierten Vektor der Eigenschaft `mediaPlayerItemConfig.subscribeTags` zu.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Erstellen Sie einen leeren String-Vektor.

   ```js
   var adTags= [];
   ```

1. hinzufügen Sie den benutzerdefinierten Tag-Namen für die Anzeige diesem Vektor an.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Weisen Sie den aktualisierten Vektor der Eigenschaft `mediaPlayerItemConfig.adTags` zu.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Verwenden Sie beim Laden des Medienstreams die Medienplayer-Elementkonfiguration.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

