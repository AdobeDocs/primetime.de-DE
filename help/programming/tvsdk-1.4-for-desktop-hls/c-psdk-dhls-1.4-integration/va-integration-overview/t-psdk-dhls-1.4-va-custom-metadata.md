---
description: Sie können mithilfe von Callback-Funktionen benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitel-Tracking-Aufrufen bereitstellen.
title: Implementieren der Unterstützung benutzerdefinierter Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Implementieren der Unterstützung benutzerdefinierter Metadaten{#implement-custom-metadata-support}

Sie können mithilfe von Callback-Funktionen benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitel-Tracking-Aufrufen bereitstellen.

Callback-Funktionen werden kurz vor dem Tracking-Aufruf aufgerufen, sodass Ihre Anwendung die für eine Anzeige oder ein Kapitel spezifischen Metadaten anhängen kann.

1. Rufen Sie Callback-Funktionen für Inhalte, Anzeigen und Kapitel auf.

   ```
   // Video Metadata Block 
   vaMetadata.videoMetadataBlock = function():Object { 
       return {"myvideoid":"1234", "mysdkversion":Version.version} 
   }; 
   
   // Ad Metadata Block invoked on every ad start 
   vaMetadata.adMetadataBlock = function(ad:Ad):Object { 
       return {"myadid":"ad-1234", "myad-sdkversion":Version.version} 
   }; 
   
   // Chapter Metadata Block invoked on every chapter start 
   vaMetadata.chapterMetadataBlock = function(chapter:VideoAnalyticsChapterData) { 
       return {"mychapterid":"chapter-1234", "mychapter-sdkversion":Version.version} 
   };
   ```
