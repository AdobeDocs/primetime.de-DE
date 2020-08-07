---
description: You can insert ads in your VOD and live/linear content by using the Adobe Primetime ad decisioning interface.
seo-description: Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.
seo-title: Werbeanforderungen
title: Werbeanforderungen
uuid: 0287f1e4-746f-42e5-b811-409064dd9b13
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Anzeigen-Timeout {#ad-timeout}

## AV Foundation-Anforderungen {#av-foundation-requirements}

Bei VOD-Inhalten sollte die Wiedergabelistenzuordnung, bei der das Manifestladen des Hauptinhalts, die Anzeigenauflösung und das Laden des Anzeigenmanifests erforderlich sind, innerhalb von 35 Sekunden abgeschlossen werden.

In case of Live content, each time the playlist is updated, playlist stitching should be completed within 20 seconds

**APIs relevant to AdResolution Timeout**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

You can set adResolutionTimeout by setting PTAdMetadata::adResolutionTimeout when setting up your ad metadata.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Thereafter follow the section: [Primetime ad server metadata](../..//tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

**APIs relevant to AdManifest Timeout**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

You can set adManifestTimeout by setting PTAdMetadata::adManifestTimeout when setting up your ad metadata.


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

Thereafter follow the section: [Primetime ad server metadata](../..//tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
