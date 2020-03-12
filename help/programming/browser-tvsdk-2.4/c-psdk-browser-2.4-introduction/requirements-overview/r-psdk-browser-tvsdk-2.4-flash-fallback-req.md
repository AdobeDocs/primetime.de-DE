---
description: Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.
seo-description: Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.
seo-title: Flash Player-Anforderungen
title: Flash Player-Anforderungen
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Flash Player-Anforderungen{#flash-player-requirements}

Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Die folgenden Anforderungen gelten für Flash Player:

* Installieren Sie mindestens Flash Player Version 23, `Primetime.js`um die Wiedergabe rückgängig zu machen.
* Um nach Updates für Flash Player Version 23 oder höher gefragt zu werden, installieren Sie mindestens Flash Player Version 11.0.0.

## Verpackungsanforderungen {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Für die Wiedergabe mit Flash Player sind die folgenden SWF-Dateien erforderlich:

* Die SWF-Hauptdatei der Anwendung, die Browser TVSDK-APIs verarbeitet.
* Die `playerProductInstall.swf` SWF-Datei, die Flash Player-Installation und -Aktualisierungen verarbeitet.

Für die Videowiedergabe in Flash ist außerdem eine Autorisierungstoken-Datei erforderlich, bei der es sich möglicherweise um eine SWF- oder eine `.DAT` Datei handelt. Der Pfad zu den SWF-Dateien, die Autorisierungstoken-Datei sowie der Name und der Typ der Tokendatei können mit den AdobePSDK-APIs angegeben werden.

Beispiel:

```js
// Set relative or http path to directory containing SWF.  
// Defaults to current directory for the html page. 
AdobePSDK.setSWFPath(<swfPath>); 
 
// Set the relative or http path to directory containing token file(s). 
// Defaults to SWFPath + "token/". 
AdobePSDK.setAuthorizationTokenPath(<authorizationTokenPath>); 
 
// Set the name of the token file, do not include any path in this string. 
AdobePSDK.setAuthorizationTokenFilename("hlsaf_localhost.swf"); 
 
//Set the token type, "DAT" or "SWF". Defaults to "DAT" 
AdobePSDK.setAuthorizationTokenType("SWF");
```

