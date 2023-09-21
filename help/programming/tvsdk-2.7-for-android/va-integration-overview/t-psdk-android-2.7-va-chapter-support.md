---
title: Implementieren der Kapitelunterstützung
description: Implementieren der Kapitelunterstützung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Implementieren der Kapitelunterstützung {#implement-chapter-support}

Sie können *custom* Kapitel für Video-Tracking in TVSDK-basierten Anwendungen.

Benutzerdefinierte Kapitel werden von der Anwendung verwaltet und basieren auf CMS-Daten oder auf einer anderen Methode, mit der die Anwendung Kapitel definiert.

>[!CAUTION]
>
>Standardkapitel werden im 2.5 Android TVSDK nicht unterstützt.

1. Definieren und verfolgen Sie benutzerdefinierte Kapitel.

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
