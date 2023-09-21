---
description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live-/Linearströme.
title: Primetime-Anzeigenserver-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Übersicht {#primetime-ad-server-metadata-overview}

TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live-/Linearströme.

## Voraussetzung

Bevor Sie Werbung in Ihren Videoinhalt aufnehmen können, geben Sie die folgenden Metadateninformationen an:

* A `mediaID`, der den jeweiligen wiederzugebenden Inhalt identifiziert.
* Ihre `zoneID`, die Ihr Unternehmen oder Ihre Website identifiziert.
* Ihre Adserver-Domäne, die die Domäne des zugewiesenen Adservers angibt.
* Andere Targeting-Parameter.

## Primetime-Anzeigenserver-Metadaten einrichten {#section_86C4A3B2DF124770B9B7FD2511394313}

Ihre Anwendung muss TVSDK mit den erforderlichen `PTAuditudeMetadata` Informationen zum Herstellen einer Verbindung zum Anzeigen-Server.

So richten Sie die Anzeigenserver-Metadaten ein:

1. Erstellen Sie eine Instanz von [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) und legen die Eigenschaften fest.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Legen Sie die `PTAuditudeMetadata` Instanz als Metadaten für die aktuelle `PTMediaPlayerItem` Metadaten mithilfe von `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Im Folgenden finden Sie ein Beispiel:

   ```
   PTMetadata *metadata = [self createMetadata]; 
   PTMediaPlayerItem *item =  
     [[[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease]; 
   
   - (PTMetadata *) createMetadata { 
       PTMetadata* metadata = [[[PTMetadata alloc] init] autorelease]; 
   
       PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
       adMetadata.zoneId = yourZoneID; 
       adMetadata.domain = yourAdServerDomain; 
   
       [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
       return metadata; 
   }
   ```
