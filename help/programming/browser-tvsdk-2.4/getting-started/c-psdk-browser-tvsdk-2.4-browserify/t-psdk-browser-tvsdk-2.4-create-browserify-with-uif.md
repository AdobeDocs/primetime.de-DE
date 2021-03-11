---
description: Verwenden Sie die Browser TVSDK-Bibliotheksdateien in Ihrer App, um einen Browser-kompatiblen Player mit dem UI-Framework zu erstellen.
title: Erstellen Sie einen mit BrowserSerify kompatiblen Player mithilfe des UI-Frameworks
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Erstellen Sie einen mit BrowserSerify kompatiblen Player mit dem UI-Framework {#create-a-browserify-compatible-player-using-the-ui-framework}

Verwenden Sie die Browser TVSDK-Bibliotheksdateien in Ihrer App, um einen Browser-kompatiblen Player mit dem UI-Framework zu erstellen.

Beispiel-Browserify-Dateien im TVSDK:

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Zum Erstellen einer mit BrowserSerify kompatiblen App mithilfe des UI-Frameworks müssen Sie im App-Code die beiden BrowserSerify-Module (bereitgestellt von Browser TVSDK) `require` verwenden:

1. BrowserSerify-Module erforderlich:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Fahren Sie mit der Entwicklung fort, wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md) beschrieben.
>Sie können Ihre App-Dateien jetzt mit &quot;Durchsuchen&quot;bündeln.
