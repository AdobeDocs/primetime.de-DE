---
description: Verwenden Sie die Bibliotheksdateien des Browsers TVSDK in Ihrer App zum Durchsuchen, um mithilfe des UI-Frameworks einen mit Browserfy kompatiblen Player zu erstellen.
title: Erstellen eines mit Browserfy kompatiblen Players mithilfe des UI-Frameworks
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Erstellen eines mit Browserfy kompatiblen Players mithilfe des UI-Frameworks {#create-a-browserify-compatible-player-using-the-ui-framework}

Verwenden Sie die Bibliotheksdateien des Browsers TVSDK in Ihrer App zum Durchsuchen, um mithilfe des UI-Frameworks einen mit Browserfy kompatiblen Player zu erstellen.

Beispiele für Browserify-Dateien, die im TVSDK enthalten sind:

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Um eine mit Browserfy kompatible App mithilfe des UI-Frameworks zu erstellen, müssen Sie `require` die beiden Browserify-Module (bereitgestellt von Browser TVSDK) in Ihrem App-Code:

1. Require Browserify modules:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Fahren Sie mit der Entwicklung fort, wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>Sie können Ihre App-Dateien jetzt mit Browserify bündeln.
