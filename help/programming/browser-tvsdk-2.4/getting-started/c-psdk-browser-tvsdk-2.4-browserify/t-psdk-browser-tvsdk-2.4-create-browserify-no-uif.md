---
description: Verwenden Sie die Browser TVSDK-Bibliotheksdatei in Ihrer App, um einen Browser-kompatiblen Player zu erstellen.
seo-description: Verwenden Sie die Browser TVSDK-Bibliotheksdatei in Ihrer App, um einen Browser-kompatiblen Player zu erstellen.
seo-title: Erstellen Sie einen mit BrowserSerify kompatiblen Player ohne UI-Framework
title: Erstellen Sie einen mit BrowserSerify kompatiblen Player ohne UI-Framework
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Erstellen Sie einen mit BrowserSerify kompatiblen Player ohne UI-Framework{#create-a-browserify-compatible-player-without-the-ui-framework}

Verwenden Sie die Browser TVSDK-Bibliotheksdatei in Ihrer App, um einen Browser-kompatiblen Player zu erstellen.

Das Thema [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) Liste den Satz von Browser TVSDK-Bibliotheken, die Sie normalerweise einschließen, wenn Sie einen einfachen Videoplayer erstellen. Dazu fügen Sie einfach `script` Tags mit `src` Attributen hinzu, die auf die Bibliotheken verweisen.

Der Vorgang unterscheidet sich geringfügig von der Erstellung eines mit BrowserSerify kompatiblen Players. Dazu verwenden Sie den `require` Befehl, um die (vom Browser TVSDK bereitgestellte) [!DNL AdobePSDK.module.js] Datei in Ihre App einzuschließen. Diese Datei bündelt die grundlegenden Player-Bibliotheksdateien in der richtigen Reihenfolge der Abhängigkeiten und gibt den `AdobePSDK` Namensraum zurück, den Sie zur Implementierung der Player-Funktionen verwenden.

Browser TVSDK bietet die folgende Beispielanwendung zum Durchsuchen und Erstellen von Dateien im Versionspaket:

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

So erstellen Sie einen mit BrowserSerify kompatiblen Videoplayer:

1. Die mit dem BrowserSerify-kompatible Bibliotheksdatei, die den `AdobePSDK` Namensraum zurückgibt, muss wie folgt aussehen:

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Erstellen Sie Ihren Player wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   Schritt 1 in dieser Aufgabe ersetzt den Schritt in den Anweisungen für den einfachen Player, in dem Sie die einzelnen grundlegenden Player-Bibliotheken in Ihrer App-Datei bereitstellen.
Sie können Ihre App-Dateien jetzt mit &quot;Durchsuchen&quot;bündeln.
