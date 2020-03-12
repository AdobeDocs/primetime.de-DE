---
description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-title: Unterstützung benutzerdefinierter Metadaten implementieren
title: Unterstützung benutzerdefinierter Metadaten implementieren
uuid: 229681f5-ff77-4321-8022-b8ccf2928fb3
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Unterstützung benutzerdefinierter Metadaten implementieren {#implement-custom-metadata-support}

Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.

Rückruffunktionen werden unmittelbar vor dem Rückverfolgungsaufruf aufgerufen, sodass Ihre Anwendung die spezifischen Metadaten zu einer Anzeige oder einem Kapitel hinzufügen kann.

1. Rufen Sie Rückruffunktionen für Inhalte, Anzeigen und Kapitel auf.

   ```
   // Video Metadata Block 
       vaTrackingMetadata.videoMetadataBlock = ^NSDictionary *() 
       { 
           return @{ 
                    @"myvideoid": @"1234", 
                    @"mysdkversion": [PTSDK apiVersion] 
                    }; 
       }; 
   
   // Ad Metadata Block invoked on every ad start 
       vaTrackingMetadata.adMetadataBlock = ^NSDictionary *(PTAd *ad) 
       { 
           return @{ 
                    @"myadid": @"ad-1234", 
                    @"myad-sdkversion": [PTSDK apiVersion] 
                    }; 
       }; 
   
   // Chapter Metadata Block invoked on every chapter start 
       vaTrackingMetadata.chapterMetadataBlock = ^NSDictionary *(PTVideoAnalyticsChapterData *chapter) 
       { 
           return @{ 
                    @"mychapterid": @"chapter-1234", 
                    @"mychapter-sdkversion": [PTSDK apiVersion] 
                    }; 
       };
   ```
