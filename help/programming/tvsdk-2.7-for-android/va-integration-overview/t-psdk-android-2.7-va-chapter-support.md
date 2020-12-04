---
description: 'null'
seo-description: 'null'
seo-title: Kapitelunterstützung implementieren
title: Kapitelunterstützung implementieren
uuid: f62a8244-6393-4a38-9ae2-8ac31f6a8a06
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Kapitelunterstützung {#implement-chapter-support} implementieren

Sie können *benutzerspezifische* Kapitel für die Videoverfolgung in TVSDK-basierten Anwendungen definieren und verfolgen.

Benutzerspezifische Kapitel werden von der Anwendung verwaltet und basieren auf CMS-Daten oder auf einer anderen Methode, die die Anwendung zum Definieren von Kapiteln verwendet.

>[!CAUTION]
>
>Standardkapitel werden im 2.5 Android TVSDK nicht unterstützt.

1. Definieren und verfolgen Sie benutzerspezifische Kapitel.

   ```java
   // First, enable chapter tracking by setting   
   // enableChapterTracking to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide  
   // an array list of chapters through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters =  
     new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   ```

