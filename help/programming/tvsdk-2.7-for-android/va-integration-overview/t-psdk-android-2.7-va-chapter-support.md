---
title: Kapitelunterstützung implementieren
description: Kapitelunterstützung implementieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '60'
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

