---
description: Sie können eigene Opportunity-Detektoren implementieren, indem Sie die Schnittstelle PlacementOpportunityDetector implementieren.
seo-description: Sie können eigene Opportunity-Detektoren implementieren, indem Sie die Schnittstelle PlacementOpportunityDetector implementieren.
seo-title: Implementieren eines benutzerdefinierten Opportunitätsdetektors
title: Implementieren eines benutzerdefinierten Opportunitätsdetektors
uuid: 012527c5-4ef0-4cd6-a9df-2fb861078a7e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 2%

---


# Implementieren eines benutzerdefinierten Opportunitätsdetektors {#implement-a-custom-opportunity-detector}

Sie können eigene Opportunity-Detektoren implementieren, indem Sie die Schnittstelle PlacementOpportunityDetector implementieren.

1. Erstellen Sie eine benutzerdefinierte `AdvertisingFactory`-Instanz und überschreiben Sie `createOpportunityDetector`. Beispiel:

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

1. Registrieren Sie die Client-Factory der Anzeige bei `MediaPlayer`. Beispiel:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Erstellen Sie eine benutzerdefinierte Opportunitätsdetektorklasse, die die `PlacementOpportunityDetector`-Klasse erweitert.
   1. Überschreiben Sie im benutzerdefinierten Opportunitätsdetektor diese Funktion:

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      Die `timedMetadataList` enthält die Liste der verfügbaren `TimedMetadata`, die sortiert wird. Metadaten enthalten die Targeting-Parameter und die benutzerdefinierten Parameter, die an den Anzeigenanbieter gesendet werden.

   1. Erstellen Sie für jedes `TimedMetadata` ein `List<PlacementOpportunity>`. Die Liste kann leer, jedoch nicht null sein. `PlacementOpportunity` sollte die folgenden Attribute aufweisen:

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Nachdem Platzierungsmöglichkeiten für alle erkannten Metadatenobjekte erstellt wurden, geben Sie einfach die `PlacementOpportunity`-Liste zurück.

Dies ist ein Beispiel für eine benutzerdefinierte Platzierungsmöglichkeit:

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

