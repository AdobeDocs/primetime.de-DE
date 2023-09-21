---
description: Verwenden Sie die Bibliotheksdatei "Durchsuchen", die von Browser TVSDK in Ihrer App bereitgestellt wird, um einen Player zu erstellen, der mit Browserfy kompatibel ist.
title: Erstellen eines mit Browserfy kompatiblen Players ohne UI-Framework
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Erstellen eines mit Browserfy kompatiblen Players ohne UI-Framework{#create-a-browserify-compatible-player-without-the-ui-framework}

Verwenden Sie die Bibliotheksdatei &quot;Durchsuchen&quot;, die von Browser TVSDK in Ihrer App bereitgestellt wird, um einen Player zu erstellen, der mit Browserfy kompatibel ist.

Das Thema [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) listet den Satz von Browser TVSDK-Bibliotheken auf, die Sie normalerweise beim Erstellen eines einfachen Video-Players einbeziehen. Fügen Sie dazu einfach `script` Tags mit `src` -Attribute, die auf die Bibliotheken verweisen.

Der Prozess unterscheidet sich geringfügig von der Erstellung eines mit Durchsuchen kompatiblen Players. Dazu verwenden Sie die `require` -Befehl zum Einschließen der [!DNL AdobePSDK.module.js] -Datei (bereitgestellt vom Browser TVSDK) in Ihrer App. Diese Datei bündelt die grundlegenden Player-Bibliotheksdateien in der richtigen Reihenfolge der Abhängigkeiten und gibt die `AdobePSDK` -Namespace verwenden, um Funktionen für Ihren Player zu implementieren.

Browser TVSDK stellt die folgende Beispielanwendung zum Durchsuchen und Erstellen von Dateien im Release-Paket bereit:

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

So erstellen Sie einen Browser-kompatiblen Videoplayer:

1. Require the Browserfy-kompatible library file, that return the `AdobePSDK` namespace:

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. Erstellen Sie den Player wie unter [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   Schritt 1 dieser Aufgabe ersetzt den Schritt in den grundlegenden Player-Anweisungen, in denen Sie die einzelnen grundlegenden Player-Bibliotheken in Ihrer App-Datei abrufen.
Sie können Ihre App-Dateien jetzt mit Browserify bündeln.
