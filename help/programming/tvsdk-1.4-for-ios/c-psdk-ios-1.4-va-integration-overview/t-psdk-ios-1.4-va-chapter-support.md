---
description: 'null'
seo-description: 'null'
seo-title: Kapitelunterstützung implementieren
title: Kapitelunterstützung implementieren
uuid: 4224cd2e-1e16-4040-972b-92c91506408f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Kapitelunterstützung implementieren{#implement-chapter-support}

Sie können Kapitel für die Videoverfolgung in einer TVSDK-basierten Anwendung wie folgt definieren und verfolgen:

* Standardkapitel, die intern von TVSDK verwaltet werden.

   Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll-Unterbrechung als erstes Kapitel definiert.
* Benutzerspezifische Kapitel, die von der Anwendung verwaltet werden und auf CMS-Daten oder einer anderen Methode basieren, die die Anwendung zum Definieren von Kapiteln verwendet.

   Definieren und verfolgen Sie standardmäßige oder benutzerdefinierte Kapitel.

   ```
   // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
   
       vaTrackingMetadata.enableChapterTracking = YES; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata:  
   // For example, 3 chapters of 60 second duration each: 
   
       NSMutableArray *chapters = [[[NSMutableArray alloc] init] autorelease]; 
   
       int chapterDuration = 60; 
       for (int i = 0; i < 3; i++) 
       { 
           PTVideoAnalyticsChapterData *chapterData =  
             [[[PTVideoAnalyticsChapterData alloc] init] autorelease]; 
           chapterData.name = [NSString stringWithFormat:@"chapter_%d", (i+1)]; 
           chapterData.range =  
             CMTimeRangeMake(CMTimeMakeWithSeconds(i * chapterDuration, 10000),  
             CMTimeMakeWithSeconds(chapterDuration, 10000)); 
   
           [chapters addObject:chapterData]; 
       } 
   
       vaTrackingMetadata.chapters = chapters; 
   
   // For default chapters, the application must not set custom chapters on the tracking metadata  
   // and simply enable chapters to be tracked by setting the boolean value as defined above.
   ```

