---
description: Verwenden Sie die Browser TVSDK-Bibliotheksdateien in Ihrer App, um einen Browser-kompatiblen Player mit dem UI-Framework zu erstellen.
seo-description: Verwenden Sie die Browser TVSDK-Bibliotheksdateien in Ihrer App, um einen Browser-kompatiblen Player mit dem UI-Framework zu erstellen.
seo-title: Erstellen Sie einen mit BrowserSerify kompatiblen Player mithilfe des UI-Frameworks
title: Erstellen Sie einen mit BrowserSerify kompatiblen Player mithilfe des UI-Frameworks
uuid: 544fd872-5ca1-417d-8aab-69613caada0e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Erstellen Sie einen mit BrowserSerify kompatiblen Player mithilfe des UI-Frameworks {#create-a-browserify-compatible-player-using-the-ui-framework}

Verwenden Sie die Browser TVSDK-Bibliotheksdateien in Ihrer App, um einen Browser-kompatiblen Player mit dem UI-Framework zu erstellen.

Beispiel-Browserify-Dateien im TVSDK:

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Zum Erstellen einer mit BrowserSerify kompatiblen App mithilfe des UI-Frameworks müssen Sie `require` die beiden BrowserSerify-Module (vom Browser TVSDK bereitgestellt) in Ihrem App-Code verwenden:

1. BrowserSerify-Module erforderlich:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Fahren Sie mit der Entwicklung fort, wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>Sie können Ihre App-Dateien jetzt mit &quot;Durchsuchen&quot;bündeln.
