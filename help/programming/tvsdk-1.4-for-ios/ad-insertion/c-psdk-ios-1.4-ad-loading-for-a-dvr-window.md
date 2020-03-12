---
description: Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.
seo-description: Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.
seo-title: Anzeigen für ein DVR-Fenster laden
title: Anzeigen für ein DVR-Fenster laden
uuid: 67bc3924-3d17-4d1a-b9a7-be8d0488a970
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Anzeigen für ein DVR-Fenster laden {#load-ad-for-a-dvr-window}

Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.

Wenn ein Benutzer zu Beginn eines DVR-Streams auf Ansicht von Inhalten Beginn, löst TVSDK alle Anzeigen für den Stream zu diesem Zeitpunkt auf. Wenn der Benutzer jedoch zu einem Zeitpunkt nach dem Stream zur Ansicht von Inhalten Beginn, können Sie entscheiden, ob nur die Anzeigen aufgelöst werden sollen, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob auch Anzeigen aufgelöst werden sollen, die vor dem aktuellen Live-Point stattgefunden haben.

>[!TIP]
>
>Das Auflösen von Anzeigen nach dem aktuellen Live-Point ist schneller, aber wenn der Benutzer rückwärts sucht, verhindert diese Option, dass der Player Anzeigen wiedergibt, die zuvor angezeigt wurden.

## Steuern und Laden von Anzeigen für ein DVR-Fenster {#section_2D93E2E947644D66B6F6ED1DD6742C25}

So steuern Sie die Anzeigenladung für ein DVR-Fenster:

Um alle Anzeigen für den gesamten Stream zu laden, setzen Sie die `PTAdMetadata.enableDVRAds` Eigenschaft auf `YES`.

>[!NOTE]
>
>Der Standardwert ist `NO`und diese Option lädt Anzeigen nur vom aktuellen Live-Point.

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
