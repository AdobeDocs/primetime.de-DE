---
description: Sie können einen Browser-kompatiblen Player mit JS-Dateien erstellen, die vom Browser TVSDK bereitgestellt werden.
seo-description: Sie können einen Browser-kompatiblen Player mit JS-Dateien erstellen, die vom Browser TVSDK bereitgestellt werden.
seo-title: Browser-kompatibler Player
title: Browser-kompatibler Player
uuid: 1832c826-d5d0-41b0-852f-286c8e4fa0f3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# Übersicht {#browserify-compatible-player-overview}

Sie können einen Browser-kompatiblen Player mit JS-Dateien erstellen, die vom Browser TVSDK bereitgestellt werden.

Browser TVSDK stellt zwei mit BrowserSerify kompatible JS-Dateien bereit. Eine ist für die Verwendung mit dem AdobePSDK-Modul vorgesehen. Dies dient zum Entwickeln von Apps ohne UI-Framework. Das andere Modul ist für die Verwendung mit dem UI-Framework-Modul vorgesehen. Gibt den PTP-Namensraum zurück, den Sie zum Erstellen von Apps mit dem UI-Framework verwenden.

Um mit &quot;Browserify&quot;zu beginnen, führen Sie die folgenden Setupbefehle aus, um [!DNL final.js]-Dateien (Ihre Bundle-Datei &quot;Browserify&quot;) in den [!DNL example]-Ordnern unter [!DNL samples/browerify/reference] und [!DNL samples/browerify/ui-framework] zu erstellen:

1. Navigieren Sie zu [!DNL samples/browserify/reference/build].
1. Führen Sie die folgenden Befehle aus:

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. Navigieren Sie zu [!DNL samples/browserify/ui-framework/build].
1. Führen Sie dieselben Befehle wie in Schritt 2 aus.

Nach Abschluss dieses Setups können Sie mit dem Erstellen von Browserify-kompatiblen TVSDK-Apps fortfahren, die auf den mit dem TVSDK bereitgestellten Beispielen basieren.
