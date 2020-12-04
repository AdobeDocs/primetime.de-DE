---
description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-title: Unterstützung benutzerdefinierter Metadaten implementieren
title: Unterstützung benutzerdefinierter Metadaten implementieren
uuid: 068ef0b9-79a2-4e44-8a0a-01e9deb8e4a6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Implementieren der Unterstützung für benutzerdefinierte Metadaten {#implement-custom-metadata-support}

Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.

Rückruffunktionen werden unmittelbar vor dem Rückverfolgungsaufruf aufgerufen, sodass Ihre Anwendung die spezifischen Metadaten zu einer Anzeige oder einem Kapitel hinzufügen kann.

Rufen Sie Rückruffunktionen für Inhalte, Anzeigen und Kapitel auf.

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

