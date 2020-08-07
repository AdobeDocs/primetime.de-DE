---
description: Media streams can carry additional metadata in the form of tags in the playlist/manifest file, and this file indicates the placement of advertising. You can specify custom tag names and be notified when certain tags appear in the manifest file.
seo-description: Media streams can carry additional metadata in the form of tags in the playlist/manifest file, and this file indicates the placement of advertising. You can specify custom tag names and be notified when certain tags appear in the manifest file.
seo-title: Custom tags
title: Custom tags
uuid: 0f47bed6-2ae8-4e4b-9f6f-672020dc3265
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Overview {#custom-tags-overview}

Media streams can carry additional metadata in the form of tags in the playlist/manifest file, and this file indicates the placement of advertising. You can specify custom tag names and be notified when certain tags appear in the manifest file.

## HLS content tags {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>This feature is not available for Safari on Apple computers, because TVSDK uses the video tag, rather than Flash or MSE, to play HLS content.

TVSDK provides out-of-the-box support for specific #EXT advertising tags. Your application can use custom tags to enhance the advertising workflow or to support blackout scenarios. To support advanced workflows, TVSDK allows you to specify and subscribe to additional tags in the manifest. You can be notified when these tags appear in the manifest file.

>[!TIP]
>
>Sie können benutzerdefinierte Tags sowohl für VOD- als auch für Live-/lineare Streams abonnieren.

>[!NOTE]
>
>Wenn HLS unter Verwendung des Video-Tags in Safari wiedergegeben wird und nicht unter Verwendung von Flash-Fallback, ist diese Funktion in Safari nicht verfügbar.

## Verwenden benutzerdefinierter HLS-Tags {#section_AD032318AEF5418393D2B1DF36B0BABB}

Hier ein Beispiel für ein benutzerdefiniertes VOD-Asset:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Ihre Anwendung kann die folgenden Szenarien einrichten:

* Eine Benachrichtigung, wenn `#EXT-X-ASSET` Tags oder andere benutzerdefinierte Tag-Namen, für die Sie ein Abonnement abgeschlossen haben, in der Datei vorhanden sind.
* Fügen Sie Anzeigen ein, wenn ein `#EXT-X-AD` Tag oder ein anderer benutzerdefinierter Tag-Name im Stream gefunden wird.

Sie können die folgenden Tags als benutzerdefinierte Tags abonnieren: `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Sie werden bei der Analyse der Manifestdateien mit einem `TimedMetadata` Ereignis benachrichtigt.

There are some advertising tags, such as `EXT-X-CUE`, to which you are already subscribed. These ad tags are also used by the default opportunity generator. You can specify which ad tags are used by the default opportunity generator by setting the `adTags` property.
