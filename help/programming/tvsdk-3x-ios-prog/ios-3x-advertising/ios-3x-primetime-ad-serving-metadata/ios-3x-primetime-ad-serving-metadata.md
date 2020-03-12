---
description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-description: TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.
seo-title: Primetime-Anzeigenservermetadaten
title: Primetime-Anzeigenservermetadaten
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Übersicht {#primetime-ad-server-metadata-overview}

TVSDK unterstützt das Auflösen und Einfügen von Anzeigen für VOD- und Live/Lineare Streams.

[!PREREQUISITE] {othertype=&quot;Prequisite&quot;}

Bevor Sie Werbung in Ihren Videoinhalt aufnehmen können, geben Sie die folgenden Metadaten an:

* Eine `mediaID`, die den zu spielenden Inhalt identifiziert.
* Ihre `zoneID`, die Ihre Firma oder Website identifiziert.
* Ihre Anzeigenserverdomäne, die die Domäne des zugewiesenen Anzeigenservers angibt.
* Andere Targeting-Parameter.

## Einrichten von Primetime-Anzeigenservermetadaten {#section_86C4A3B2DF124770B9B7FD2511394313}

Ihre Anwendung muss TVSDK die erforderlichen `PTAuditudeMetadata` Informationen bereitstellen, um eine Verbindung zum Anzeigen-Server herzustellen.

So richten Sie die Ad-Server-Metadaten ein:

1. Erstellen Sie eine Instanz von [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) und legen Sie deren Eigenschaften fest.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Legen Sie die `PTAuditudeMetadata` Instanz als Metadaten für die aktuellen `PTMediaPlayerItem` Metadaten fest, indem Sie `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Hier ein Beispiel:

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
