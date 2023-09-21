---
description: Sie können Ihre eigenen Opportunity-Detektoren implementieren, indem Sie die Schnittstelle PlacementOpportunityDetector implementieren.
title: Implementieren eines benutzerdefinierten Opportunity-Detektors
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Implementieren eines benutzerdefinierten Opportunity-Detektors {#implement-a-custom-opportunity-detector}

Sie können Ihre eigenen Opportunity-Detektoren implementieren, indem Sie die Schnittstelle PlacementOpportunityDetector implementieren.

1. Benutzerdefiniert erstellen `AdvertisingFactory` Instanz und Überschreibung `createOpportunityDetector`. Beispiel:

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public PlacementOpportunityDetector createOpportunityDetector(MediaPlayerItem item) { 
           return new CustomPlacementOpportunityDetector(); 
       } 
       ... 
   }
   ```

1. Registrieren Sie die Client-Factory der Anzeige bei der `MediaPlayer`. Beispiel:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Erstellen Sie eine benutzerdefinierte Opportunity-Detektorklasse, die die `PlacementOpportunityDetector` -Klasse.
   1. Überschreiben Sie im benutzerdefinierten Opportunity-Detektor diese Funktion:

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      Die `timedMetadataList` enthält die Liste der verfügbaren `TimedMetadata`, der sortiert wird. Metadaten enthalten die Targeting-Parameter und die benutzerdefinierten Parameter, die an den Anzeigenanbieter gesendet werden.

   1. Für jeden `TimedMetadata`, erstellen Sie eine `List<PlacementOpportunity>`. Die Liste kann leer, aber nicht null sein. `PlacementOpportunity` sollte die folgenden Attribute aufweisen:

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Nachdem Platzierungsmöglichkeiten für alle erkannten zeitgesteuerten Metadatenobjekte erstellt wurden, geben Sie einfach die `PlacementOpportunity` Liste.

Dies ist ein Beispiel für einen benutzerdefinierten Platzierungsoptionsdetektor:

```java
public class CustomPlacementOpportunityDetector implements PlacementOpportunityDetector { 
    ... 
    @Override 
    public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata) { 
        ... 
        List<PlacementOpportunity> opportunities = new ArrayList<PlacementOpportunity>(); 
 
        for (TimedMetadata timedMetadata : timedMetadataList) { 
 
            if (isOpportunity(timedMetadata)) {        // check if given timedMetadata should be  
                                                       // considered as an opportunity 
 
                // create an object of PlacementOpportunity and add it to the opportunities list 
                PlacementOpportunity opportunity =  
                  createPlacementOpportunity(timedMetadata, airingId, metadata); 
                Opportunities.add(opportunity); 
            } 
        } 
        return opportunities; 
    }    
    ... 
} 
```
