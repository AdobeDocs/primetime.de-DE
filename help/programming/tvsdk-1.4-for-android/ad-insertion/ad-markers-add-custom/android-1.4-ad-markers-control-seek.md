---
description: Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
seo-description: Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
seo-title: Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken
title: Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken
uuid: cf973caf-be29-46ce-bfa4-651e7653f8d4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Sie können das Standardverhalten für die Suche von TVSDK nach Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.

Standardmäßig überspringt TVSDK die Anzeigen, wenn ein Benutzer in Abschnitte der Anzeige, die sich aus der Platzierung benutzerspezifischer Anzeigenmarken ergeben, einspringt oder sie vergangene Abschnitte durchsucht. Dies kann sich von dem aktuellen Wiedergabeverhalten bei Standard-Werbeunterbrechungen unterscheiden.

Sie können TVSDK anweisen, die Abspielleiste an den Anfang der zuletzt übersprungenen benutzerdefinierten Anzeige zu verschieben, wenn der Benutzer nach einer oder mehreren benutzerdefinierten Anzeigen sucht.

1. Konfigurieren Sie eine Metadateninstanz mit der `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` Auflistung, die auf den Zeichenfolgenwert &quot;true&quot;gesetzt ist (nicht als boolescher Wert `true`).

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. Erstellen und konfigurieren Sie eine `MediaResource` Instanz und übergeben Sie die zusätzlichen Konfigurationsoptionen an `TimeRangeCollection.toMetadata`. Diese Methode erhält zusätzliche Konfigurationsoptionen über eine andere generische Metadatenstruktur.

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```

