---
description: 'null'
seo-description: 'null'
seo-title: Kapitelunterstützung implementieren
title: Kapitelunterstützung implementieren
uuid: 5b39e494-85ad-43bb-ab56-a55797aa4ef7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Kapitelunterstützung {#implement-chapter-support} implementieren

Sie können Kapitel für die Videoverfolgung in einer TVSDK-basierten Anwendung wie folgt definieren und verfolgen:

* Standardkapitel, die intern von TVSDK verwaltet werden.

   Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll-Unterbrechung als erstes Kapitel definiert.
* Benutzerspezifische Kapitel, die von der Anwendung verwaltet werden und auf CMS-Daten oder einer anderen Methode basieren, die die Anwendung zum Definieren von Kapiteln verwendet.

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
