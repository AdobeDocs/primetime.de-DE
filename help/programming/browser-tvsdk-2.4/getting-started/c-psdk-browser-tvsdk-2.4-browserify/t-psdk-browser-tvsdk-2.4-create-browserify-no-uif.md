---
description: Verwenden Sie die Browser TVSDK-Bibliotheksdatei in Ihrer App, um einen Browser-kompatiblen Player zu erstellen.
title: Erstellen Sie einen mit BrowserSerify kompatiblen Player ohne UI-Framework
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Erstellen Sie einen BrowserSerify-kompatiblen Player ohne UI-Framework{#create-a-browserify-compatible-player-without-the-ui-framework}

Verwenden Sie die Browser TVSDK-Bibliotheksdatei in Ihrer App, um einen Browser-kompatiblen Player zu erstellen.

Das Thema [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) Liste den Satz von Browser TVSDK-Bibliotheken, die Sie normalerweise einschließen, wenn Sie einen Video-Player erstellen. Dazu fügen Sie einfach `script` Tags mit `src` Attributen hinzu, die auf die Bibliotheken zeigen.

Der Vorgang unterscheidet sich geringfügig von der Erstellung eines mit BrowserSerify kompatiblen Players. Dazu verwenden Sie den Befehl `require`, um die [!DNL AdobePSDK.module.js]-Datei (die vom Browser TVSDK bereitgestellt wird) in Ihre App einzuschließen. Diese Datei bündelt die grundlegenden Player-Bibliotheksdateien in der richtigen Reihenfolge der Abhängigkeiten und gibt den `AdobePSDK`-Namensraum zurück, den Sie zur Implementierung der Player-Funktionen verwenden.

Browser TVSDK bietet die folgende Beispielanwendung zum Durchsuchen und Erstellen von Dateien im Versionspaket:

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

So erstellen Sie einen mit BrowserSerify kompatiblen Videoplayer:

1. Die mit dem BrowserSerify-kompatible Bibliotheksdatei anfordern, die den Namensraum `AdobePSDK` zurückgibt:

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Erstellen Sie den Player wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) beschrieben.

   Schritt 1 in dieser Aufgabe ersetzt den Schritt in den Anweisungen für den einfachen Player, in dem Sie die einzelnen grundlegenden Player-Bibliotheken in Ihrer App-Datei bereitstellen.
Sie können Ihre App-Dateien jetzt mit &quot;Durchsuchen&quot;bündeln.
