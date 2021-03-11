---
title: Kapitelunterstützung implementieren
description: Kapitelunterstützung implementieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---


# Kapitelunterstützung implementieren{#implement-chapter-support}

Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll-Unterbrechung als erstes Kapitel definiert. Sie können Kapitel für die Videoverfolgung in einer Browser TVSDK-basierten Anwendung mit benutzerdefinierten Kapiteln definieren und verfolgen. Benutzerspezifische Kapitel werden von der Anwendung verwaltet und basieren auf CMS-Daten oder einer anderen Methode, die die Anwendung zum Definieren von Kapiteln verwendet.

1. Definieren und verfolgen Sie benutzerspezifische Kapitel.

   ```js
   vaObj.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata: 
   // For example: 3 chapters of 60 second duration each 
   var chapters = []; 
   var chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       var chapterData = new AdobePSDK.VA.VideoAnalyticsChapterData("chapter_" + (i+1), i * chapterDuration, chapterDuration, (i+1)); 
       chapters.push(chapterData); 
   } 
   
   vaObj.chapters = chapters;
   ```

