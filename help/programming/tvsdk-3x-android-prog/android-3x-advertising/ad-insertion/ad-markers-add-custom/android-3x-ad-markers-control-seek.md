---
description: Sie können das Standardverhalten für den Umgang von TVSDK mit Suchvorgängen über Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.
title: Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Steuern des Wiedergabeverhaltens für die Suche nach benutzerdefinierten Anzeigenmarken {#control-playback-behavior-for-seeking-over-custom-ad-markers}

Sie können das Standardverhalten für den Umgang von TVSDK mit Suchvorgängen über Anzeigen überschreiben, wenn Sie benutzerdefinierte Anzeigenmarken verwenden.

Standardmäßig überspringt TVSDK die Anzeigen, wenn ein Benutzer in Abschnitte der Anzeige, die sich aus der Platzierung benutzerspezifischer Anzeigenmarken ergeben, einspringt oder sie vergangene Abschnitte durchsucht. Dies kann sich von dem aktuellen Wiedergabeverhalten bei Standard-Werbeunterbrechungen unterscheiden. Sie können TVSDK so einstellen, dass die Abspielleiste an den Anfang der zuletzt übersprungenen benutzerdefinierten Anzeige verschoben wird, wenn der Benutzer nach einer oder mehreren benutzerdefinierten Anzeigen sucht.

1. Rufen Sie `CustomRangeMetadata.setAdjustSeekPosition` mit `true` auf.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. Verwenden Sie `customRangeMetadata` in `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
