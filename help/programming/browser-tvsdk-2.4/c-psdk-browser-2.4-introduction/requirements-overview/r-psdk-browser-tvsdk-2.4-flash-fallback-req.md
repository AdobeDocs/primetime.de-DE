---
description: Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.
title: Flash Player
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Flash Player{#flash-player-requirements}

Um Flash Player zu verwenden, stellen Sie sicher, dass Ihre Umgebung die erforderlichen Anforderungen erfüllt.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Hier finden Sie die Anforderungen für die Flash Player:

* So spielen Sie mit `Primetime.js`, installieren Sie mindestens Flash Player Version 23.
* Um nach Updates auf Flash Player-Version 23 oder höher gefragt zu werden, installieren Sie mindestens Flash Player-Version 11.0.0.

## Verpackungsanforderungen {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Die Wiedergabe mit Flash Player erfordert die folgenden SWF-Dateien:

* Die Hauptanwendungs-SWF-Datei, die Browser TVSDK-APIs verarbeitet.
* Die `playerProductInstall.swf` SWF-Datei, die Flash Player installiert und aktualisiert.

Darüber hinaus erfordert die Videowiedergabe auf Flash eine Autorisierungstoken-Datei, die eine SWF oder eine `.DAT` -Datei. Der Pfad zu den SWF-Dateien, die Autorisierungstoken-Datei sowie der Name und Typ der Token-Datei können mithilfe der AdobePSDK-APIs angegeben werden.

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
