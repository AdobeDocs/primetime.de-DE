---
description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
title: Unterstützung benutzerdefinierter Metadaten implementieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Implementieren der Unterstützung für benutzerdefinierte Metadaten {#implement-custom-metadata-support}

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
