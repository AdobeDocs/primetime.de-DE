---
description: Sie können das Standardverhalten für die Verarbeitung von Suchanzeigen durch TVSDK bei der Verwendung benutzerspezifischer Anzeigenmarken überschreiben.
title: Verhalten der Wiedergabe bei der Suche über benutzerdefinierte Anzeigenmarken steuern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Verhalten der Wiedergabe bei der Suche über benutzerdefinierte Anzeigenmarken steuern {#control-playback-behavior-for-seeking-over-custom-ad-markers}

Sie können das Standardverhalten für die Verarbeitung von Suchanzeigen durch TVSDK bei der Verwendung benutzerspezifischer Anzeigenmarken überschreiben.

Standardmäßig überspringt TVSDK die Anzeigen, wenn ein Benutzer nach Bereichen sucht, die sich aus der Platzierung benutzerspezifischer Anzeigenmarkierungen ergeben, oder diese vergangene Abschnitte. Dies kann vom aktuellen Wiedergabe-Verhalten bei standardmäßigen Werbeunterbrechungen abweichen. Sie können TVSDK so einstellen, dass die Abspielleiste an den Anfang der zuletzt übersprungenen benutzerdefinierten Anzeige verschoben wird, wenn der Benutzer nach einer oder mehreren benutzerdefinierten Anzeigen sucht.

1. Aufruf `CustomRangeMetadata.setAdjustSeekPosition` mit `true`.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. Verwendung `customRangeMetadata` in `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
