---
description: Sie können mithilfe von Callback-Funktionen benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitel-Tracking-Aufrufen bereitstellen.
title: Implementieren der Unterstützung benutzerdefinierter Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Implementieren der Unterstützung benutzerdefinierter Metadaten {#implement-custom-metadata-support}

Sie können mithilfe von Callback-Funktionen benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitel-Tracking-Aufrufen bereitstellen.

Callback-Funktionen werden kurz vor dem Tracking-Aufruf aufgerufen, sodass Ihre Anwendung die für eine Anzeige oder ein Kapitel spezifischen Metadaten anhängen kann.

Rufen Sie Callback-Funktionen für Inhalte, Anzeigen und Kapitel auf.

```java
// Video Metadata Block 
vaMetadata.setVideoMetadataBlock(new VideoAnalyticsMetadata.VideoMetadataBlock() { 
    @Override 
    public HashMap<String, String> call() { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myvideoid", "1234"); 
        result.put("mysdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Ad Metadata Block invoked on every ad start 
vaMetadata.setAdMetadataBlock(new VideoAnalyticsMetadata.AdMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(Ad ad) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myadid", "ad-1234"); 
        result.put("myad-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Chapter Metadata Block invoked on every chapter start 
vaMetadata.setChapterMetadataBlock(new VideoAnalyticsMetadata.ChapterMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(VideoAnalyticsChapterData chapter) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("mychapterid", "chapter-1234"); 
        result.put("mychapter-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
});
```
