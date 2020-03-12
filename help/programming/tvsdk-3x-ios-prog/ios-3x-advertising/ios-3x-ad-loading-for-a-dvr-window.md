---
description: Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.
seo-description: Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.
seo-title: Anzeigen für ein DVR-Fenster laden
title: Anzeigen für ein DVR-Fenster laden
uuid: 3ae1fbf6-deae-4f39-a17d-43d1fe3cb975
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Anzeigen für ein DVR-Fenster laden {#load-ad-for-a-dvr-window}

Sie können entscheiden, ob Sie nur die Anzeigen auflösen möchten, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob Sie Anzeigen auflösen möchten, die vor dem aktuellen Live-Point erscheinen.

Wenn ein Benutzer zu Beginn eines DVR-Streams auf Ansicht von Inhalten Beginn, löst TVSDK alle Anzeigen für den Stream zu diesem Zeitpunkt auf. Wenn der Benutzer jedoch zu einem Zeitpunkt nach dem Stream zur Ansicht von Inhalten Beginn, können Sie entscheiden, ob nur die Anzeigen aufgelöst werden sollen, die nach dem aktuellen Live-Point des Benutzers auftreten, oder ob auch Anzeigen aufgelöst werden sollen, die vor dem aktuellen Live-Point stattgefunden haben.

>[!TIP]
>
>Das Auflösen von Anzeigen nach dem aktuellen Live-Point ist schneller, aber wenn der Benutzer rückwärts sucht, verhindert diese Option, dass der Player Anzeigen wiedergibt, die zuvor angezeigt wurden.

## Steuern und Laden von Anzeigen für ein DVR-Fenster {#section_2D93E2E947644D66B6F6ED1DD6742C25}

So steuern Sie die Anzeigenladung für ein DVR-Fenster:

    Um alle Anzeigen für den gesamten Stream zu laden, setzen Sie die Eigenschaft &quot;PTAdMetadata.enableDVRAds&quot;auf &quot;YES&quot;.

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
