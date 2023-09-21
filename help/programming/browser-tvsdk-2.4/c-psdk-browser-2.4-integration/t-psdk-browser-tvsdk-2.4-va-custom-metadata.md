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

   ```js
   vaObj.videoMetadataBlock = function() { 
       return { 
           "name" : "my-video", 
           "genre" : "comedy" 
       }; 
   } 
   
   vaObj.adMetadataBlock = function(ad) { 
       return { 
           "name" : "my-ad", 
           "category" : "automotive" 
       }; 
   } 
   
   vaObj.chapterMetadataBlock = function(chapter) { 
       return { 
           "name" : "my-chapter", 
           "type" : "quartile" 
       }; 
   }
   ```
