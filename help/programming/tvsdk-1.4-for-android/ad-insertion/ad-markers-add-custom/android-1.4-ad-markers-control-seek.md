---
description: Sie können das Standardverhalten für die Suche von TVSDK über Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
title: Verhalten der Wiedergabe bei der Suche über benutzerdefinierte Anzeigenmarken steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Verhalten der Wiedergabe bei der Suche über benutzerdefinierte Anzeigenmarken steuern{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Sie können das Standardverhalten für die Suche von TVSDK über Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.

Standardmäßig überspringt TVSDK die Anzeigen, wenn ein Benutzer nach Bereichen sucht, die sich aus der Platzierung benutzerspezifischer Anzeigenmarkierungen ergeben, oder diese vergangene Abschnitte. Dies kann vom aktuellen Wiedergabe-Verhalten bei standardmäßigen Werbeunterbrechungen abweichen.

Sie können TVSDK anweisen, die Abspielleiste an den Anfang der zuletzt übersprungenen benutzerdefinierten Anzeige zu verschieben, wenn der Benutzer nach einer oder mehreren benutzerdefinierten Anzeigen sucht.

1. Konfigurieren Sie eine Metadateninstanz mit der `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` Auflistung, die auf den Zeichenfolgenwert &quot;true&quot;gesetzt ist (nicht als boolescher Wert) `true`).

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. Erstellen und konfigurieren Sie eine `MediaResource` -Instanz, die die zusätzlichen Konfigurationsoptionen an `TimeRangeCollection.toMetadata`. Diese Methode erhält zusätzliche Konfigurationsoptionen über eine andere generische Metadatenstruktur.

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```
