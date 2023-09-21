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

Rufen Sie Callback-Funktionen für Inhalte, Anzeigen und Kapitel auf.

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
