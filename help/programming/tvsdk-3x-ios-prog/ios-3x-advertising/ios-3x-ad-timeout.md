---
description: Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.
seo-description: Sie können Anzeigen in Ihre VOD- und Live-/Linearinhalte einfügen, indem Sie die Adobe Primetime-Benutzeroberfläche für die Anzeigenentscheidung verwenden.
seo-title: Werbeanforderungen
title: Werbeanforderungen
uuid: 0287f1e4-746f-42e5-b811-409064dd9b13
translation-type: tm+mt
source-git-commit: 48ad8aad89701f8414e752a4d4e41da252d28d62
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Anzeigentimeout {#ad-timeout}

## AV Foundation-Anforderungen {#av-foundation-requirements}

Bei VOD-Inhalten sollte die Wiedergabelistenzuordnung, bei der das Manifestladen des Hauptinhalts, die Anzeigenauflösung und das Laden des Anzeigenmanifests erforderlich sind, innerhalb von 35 Sekunden abgeschlossen werden.

Bei Live-Inhalten sollte jedes Mal, wenn die Wiedergabeliste aktualisiert wird, die Synchronisierung der Wiedergabeliste innerhalb von 20 Sekunden abgeschlossen werden

**Für AdResolution-Timeout relevante APIs**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

Sie können adResolutionTimeout festlegen, indem Sie PTAdMetadata::adResolutionTimeout festlegen, wenn Sie Ihre Anzeigenmetadaten einrichten.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Folgen Sie anschließend dem Abschnitt: [Primetime-Anzeigenserver-Metadaten](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

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

Folgen Sie anschließend dem Abschnitt: [Primetime-Anzeigenserver-Metadaten](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
