---
description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-description: Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.
seo-title: Unterstützung benutzerdefinierter Metadaten implementieren
title: Unterstützung benutzerdefinierter Metadaten implementieren
uuid: 4a59f923-3e5b-4bad-b9d8-ee43886f549f
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Unterstützung benutzerdefinierter Metadaten implementieren {#implement-custom-metadata-support}

Mithilfe von Rückruffunktionen können Sie benutzerdefinierte Metadaten zu Inhalts-, Anzeigen- und Kapitelverfolgungsaufrufen bereitstellen.

Rückruffunktionen werden unmittelbar vor dem Rückverfolgungsaufruf aufgerufen, sodass Ihre Anwendung die spezifischen Metadaten zu einer Anzeige oder einem Kapitel hinzufügen kann.

1. Rufen Sie Rückruffunktionen für Inhalte, Anzeigen und Kapitel auf.

   ```java
   // Video Metadata Block 
   // In a separate public class Implement an instance  
   // of VideoAnalyticsMetadata.VideoMetadataBlock 
   
   public class VideoMetadataBlockImpl  
     implements VideoAnalyticsMetadata.VideoMetadataBlock { 
   
       private final String video_id; 
       private final String player_version; 
   
       public VideoMetadataBlockImpl(String id, String version) { 
           this.video_id = id == null ? "" : id; 
           this.player_version = version == null ? "" : version; 
       } 
       @Override 
       public HashMap<String, String> call() { 
           HashMap<String, String> result = new HashMap<String, String>(); 
           result.put("videoid", video_id); 
           result.put("mysdkversion", player_version); 
           return result;   
       } 
   } 
   // Create an instance of the above created  
   // public class and assign it to vaMetadata 
   vaMetadata.setVideoMetadataBlock( 
     new VideoMetadataBlockImpl("1234", "1.2.3.4")); 
   
   // Ad Metadata Block that is invoked on every ad start 
   // In a separate public class Implement an instance of  
   // VideoAnalyticsMetadata.AdMetadataBlock 
   
   public class AdMetadataBlockImpl  
     implements VideoAnalyticsMetadata.AdMetadataBlock { 
   
       private final String ad_id; 
       private final String ad_sdkversion;
   
       public AdMetadataBlockImpl(String id, String version) { 
           this.ad_id = id == null ? "" : id; 
           this.ad_sdkversion = version == null ? "" : version; 
       } 
   
       @Override 
       public HashMap<String, String> call() { 
           HashMap<String, String> result = new HashMap<String, String>();\ 
           result.put("myadid", ad_id); 
           result.put("myad-sdkversion", ad_sdkversion); 
           return result; 
       } 
   } 
   // Create an instance of above created  
   // public class and assign it to vaMetadata 
   vaMetadata.setAdMetadataBlock( 
     new AdMetadataBlockImpl("ad-1234", "1.2.3.4")); 
   
   // Chapter Metadata Block that is invoked on every chapter start 
   // In a separate public class Implement an instance of  
   // VideoAnalyticsMetadata.ChapterMetadataBlock 
   
   public class ChapterMetadataBlockImpl  
     implements VideoAnalyticsMetadata.ChapterMetadataBlock { 
   
       private final String chapter_id; 
       private final String chapter_sdkversion; 
   
       public ChapterMetadataBlockImpl(String id, String version) { 
   
           this.chapter_id = id == null ? "" : id; 
           this.chapter_sdkversion = version == null ? "" : version; 
       } 
   
       @Override 
       public HashMap<String, String> call() { 
   
           HashMap<String, String> result = new HashMap<String, String>(); 
           result.put("mychapterid", chapter_id); 
           result.put("mychapter-sdkversion", chapter_sdkversion); 
           return result; 
   
           } 
   } 
   // Create an instance of above created public class and  
   // assign it to vaMetadata 
   vaMetadata.setChapterMetadataBlock( 
     new ChapterMetadataBlockImpl("chapter-1234", "1.2.3.4")); 
   ```

