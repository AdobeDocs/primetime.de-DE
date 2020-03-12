---
description: 'null'
seo-description: 'null'
seo-title: Kapitelunterstützung implementieren
title: Kapitelunterstützung implementieren
uuid: 85d14b83-7910-4f5d-9ef2-511de916abd6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Kapitelunterstützung implementieren {#implement-chapter-support}

Sie können Kapitel für die Videoverfolgung in einer TVSDK-basierten Anwendung wie folgt definieren und verfolgen:

* Standardkapitel, die intern von TVSDK verwaltet werden.

   Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll-Unterbrechung als erstes Kapitel definiert.
* Benutzerspezifische Kapitel, die von der Anwendung verwaltet werden und auf CMS-Daten oder einer anderen Methode basieren, die die Anwendung zum Definieren von Kapiteln verwendet.

   Definieren und verfolgen Sie standardmäßige oder benutzerdefinierte Kapitel.

   ```
   // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
   
       vaMetadata.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata:  
   // For example: 3 chapters of 60 second duration each 
   
       var chapters:Vector.<VideoAnalyticsChapterData> = new Vector.<VideoAnalyticsChapterData>(); 
       var chapterDuration:int = 60; 
       for (var i:int = 0; i < 3; i++) { 
           var chapterData:VideoAnalyticsChapterData =  
             new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration); 
           chapterData.name = "chapter_%d" + (i+1); 
   
           chapters.push(chapterData); 
       } 
   
       vaMetadata.chapters = chapters; 
   
   // For default chapters, the application must not set custom chapters on the tracking metadata  
   // and simply enable chapters to be tracked by setting the boolean value as defined above. 
   ```

