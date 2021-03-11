---
description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
title: Unterstützung benutzerdefinierter Metadaten implementieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Implementieren der Unterstützung für benutzerdefinierte Metadaten{#implement-custom-metadata-support}

Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.

Rückruffunktionen werden unmittelbar vor dem Rückverfolgungsaufruf aufgerufen, sodass Ihre Anwendung die spezifischen Metadaten zu einer Anzeige oder einem Kapitel hinzufügen kann.

1. Rufen Sie Rückruffunktionen für Inhalte, Anzeigen und Kapitel auf.

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

