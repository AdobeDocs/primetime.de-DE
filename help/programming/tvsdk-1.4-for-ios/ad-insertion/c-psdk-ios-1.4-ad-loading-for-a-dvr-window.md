---
description: Sie können entscheiden, ob nur die Anzeigen aufgelöst werden sollen, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Anzeigen, die vor dem aktuellen Live-Point erscheinen, aufgelöst werden sollen.
title: Anzeigen für ein DVR-Fenster laden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Anzeigen für ein DVR-Fenster laden {#load-ad-for-a-dvr-window}

Sie können entscheiden, ob nur die Anzeigen aufgelöst werden sollen, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Anzeigen, die vor dem aktuellen Live-Point erscheinen, aufgelöst werden sollen.

Wenn ein Benutzer beginnt, Inhalte zu Beginn eines DVR-Streams anzuzeigen, löst TVSDK alle Anzeigen für den Stream zu diesem Zeitpunkt auf. Wenn der Benutzer jedoch beginnt, Inhalte zu einem Zeitpunkt nach dem Anfang des Streams anzuzeigen, können Sie entscheiden, ob nur die Anzeigen aufgelöst werden sollen, die nach dem aktuellen Live-Point des Benutzers auftreten, oder auch Anzeigen, die vor dem aktuellen Live-Point stattgefunden haben.

>[!TIP]
>
>Das Auflösen von Anzeigen nach dem aktuellen Live-Point ist schneller. Wenn der Benutzer jedoch nach hinten springt, verhindert diese Option, dass der Player Anzeigen wiedergibt, die zuvor erschienen sind.

## Steuern und Laden von Anzeigen für ein DVR-Fenster {#section_2D93E2E947644D66B6F6ED1DD6742C25}

So steuern Sie die Anzeigenladung für ein DVR-Fenster:

Um alle Anzeigen für den gesamten Stream zu laden, legen Sie die `PTAdMetadata.enableDVRAds` Eigenschaft auf `YES`.

>[!NOTE]
>
>Der Standardwert ist `NO`und diese Option lädt Anzeigen nur vom aktuellen Live-Punkt.

Beispiel:

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
 
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
adMetadata.zoneId = <ZoneId>; 
adMetadata.domain = <Domain>; 
 
// Enable DVR Ads by setting to YES the enableDVRAds property on PTAdMetadata  
// (PTAuditudeMetadata is a subclass of PTAdMetadata)  
adMetadata.enableDVRAds = YES; 
 
[metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
 
//Create PTMediaPlayerItem with the previously prepared metadata    
playerItem = [[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata]; 
```
