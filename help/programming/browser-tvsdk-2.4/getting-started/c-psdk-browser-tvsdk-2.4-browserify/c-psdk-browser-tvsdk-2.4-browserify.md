---
description: Sie können einen Browser-kompatiblen Player mithilfe von JS-Dateien erstellen, die vom Browser TVSDK bereitgestellt werden.
title: Browser-kompatibler Player
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Übersicht {#browserify-compatible-player-overview}

Sie können einen Browser-kompatiblen Player mithilfe von JS-Dateien erstellen, die vom Browser TVSDK bereitgestellt werden.

Browser TVSDK stellt zwei Browserfy-kompatible JS-Dateien bereit. Eine ist für die Verwendung mit dem AdobePSDK-Modul vorgesehen. Dies dient der Entwicklung von Apps ohne UI-Framework. Die andere ist für die Verwendung mit dem UI-Framework-Modul vorgesehen. Sie gibt den PTP-Namespace zurück, den Sie zum Schreiben von Apps mit dem UI-Framework verwenden.

Führen Sie zum Einstieg in Browserify die folgenden Setup-Befehle aus, um [!DNL final.js] -Dateien (Ihre Bundle-Datei &quot;Browserfy&quot;) im [!DNL example] Verzeichnisse unter [!DNL samples/browerify/reference] und [!DNL samples/browerify/ui-framework]:

1. Navigieren Sie zu [!DNL samples/browserify/reference/build].
1. Führen Sie die folgenden Befehle aus:

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Navigieren Sie zu [!DNL samples/browserify/ui-framework/build].
1. Führen Sie dieselben Befehle wie in Schritt 2 aus.

Nach Abschluss dieser Einrichtung können Sie mit der Erstellung von Browserfy-kompatiblen TVSDK-Apps fortfahren, die auf den mit dem TVSDK bereitgestellten Beispielen basieren.
