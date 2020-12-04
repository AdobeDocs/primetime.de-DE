---
description: Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.
seo-description: Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.
seo-title: Anforderungen an Flash Player
title: Anforderungen an Flash Player
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 1%

---


# Anforderungen an Flash Player{#flash-player-requirements}

Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Die folgenden Anforderungen gelten für den Flash Player:

* Um die Wiedergabe mit `Primetime.js` wiederherzustellen, installieren Sie mindestens Flash Player Version 23.
* Um nach Updates für Flash Player Version 23 oder höher gefragt zu werden, installieren Sie mindestens Flash Player Version 11.0.0.

## Verpackungsanforderungen {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Für die Wiedergabe mit Flash Player sind die folgenden SWF-Dateien erforderlich:

* Die SWF-Hauptdatei der Anwendung, die Browser TVSDK-APIs verarbeitet.
* Die SWF-Datei `playerProductInstall.swf`, die die Installation und Aktualisierung von Flash Playern verarbeitet.

Darüber hinaus ist für die Videowiedergabe in Flash eine Autorisierungstoken-Datei erforderlich, die eine SWF- oder `.DAT`-Datei sein kann. Der Pfad zu den SWF-Dateien, die Autorisierungstoken-Datei sowie der Name und der Typ der Tokendatei können mit den AdobePSDK-APIs angegeben werden.

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

