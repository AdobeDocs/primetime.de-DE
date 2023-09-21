---
title: Implementieren der Kapitelunterstützung
description: Implementieren der Kapitelunterstützung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Implementieren der Kapitelunterstützung {#implement-chapter-support}

Sie können Kapitel für das Video-Tracking in einer TVSDK-basierten Anwendung wie folgt definieren und verfolgen:

* Standardkapitel, die intern von TVSDK verwaltet werden.

  Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll als erstes Kapitel definiert.
* Benutzerdefinierte Kapitel, die von der Anwendung verwaltet werden und auf CMS-Daten oder einer anderen Methode basieren, die die Anwendung zum Definieren von Kapiteln verwendet.

1. Definieren und verfolgen Sie standardmäßige oder benutzerdefinierte Kapitel.

   ```java
   // First, enable chapter tracking by setting  
   // the Boolean 'enableChapterTracking' to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide an array list of chapters  
   // through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters = new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   // For default chapters, the application must not set  
   // custom chapters on the tracking metadata 
   // and simply enable chapters to be tracked by setting  
   // the boolean value as defined above.
   ```
