---
description: Sie können Anzeigen in Ihren VOD- und Live-/Linearinhalt einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für Anzeigenentscheidungen verwenden.
title: Werbeanforderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Anzeigen-Timeout {#ad-timeout}

## AV Foundation-Anforderungen {#av-foundation-requirements}

Bei VOD-Inhalten sollte die Zusammenfügung der Wiedergabeliste, die das Laden des Hauptinhaltsmanifests, die Anzeigenauflösung und das Laden des Anzeigenmanifests umfasst, innerhalb von 35 Sekunden abgeschlossen werden.

Bei Live-Inhalten sollte jedes Mal, wenn die Wiedergabeliste aktualisiert wird, die Zuordnung der Wiedergabeliste innerhalb von 20 Sekunden abgeschlossen sein

**Für AdResolution-Timeout relevante APIs**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

Sie können adResolutionTimeout festlegen, indem Sie PTAdMetadata::adResolutionTimeout beim Einrichten Ihrer Anzeigenmetadaten festlegen.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Gehen Sie anschließend wie folgt vor: [Primetime-Anzeigenserver-Metadaten](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

**Für AdManifest-Timeout relevante APIs**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

Sie können adManifestTimeout festlegen, indem Sie PTAdMetadata::adManifestTimeout festlegen, wenn Sie Ihre Anzeigenmetadaten einrichten.


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

Gehen Sie anschließend wie folgt vor: [Primetime-Anzeigenserver-Metadaten](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
