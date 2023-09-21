---
title: Implementieren der Kapitelunterstützung
description: Implementieren der Kapitelunterstützung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---

# Implementieren der Kapitelunterstützung{#implement-chapter-support}

Ein Kapitel ist definiert als die Zeit zwischen den einzelnen Werbeunterbrechungen. Beispielsweise wird die Zeit zwischen einer Pre-Roll-Werbeunterbrechung und der ersten Mid-Roll als erstes Kapitel definiert. Sie können Kapitel für die Videoverfolgung in einer Browser TVSDK-basierten Anwendung mit benutzerdefinierten Kapiteln definieren und verfolgen. Benutzerdefinierte Kapitel werden von der Anwendung verwaltet und basieren auf CMS-Daten oder einer anderen Methode, mit der die Anwendung Kapitel definiert.

1. Definieren und verfolgen Sie benutzerdefinierte Kapitel.

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
