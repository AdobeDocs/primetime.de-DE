---
description: Sie können Anzeigeneinfüge-Metadaten anpassen.
title: Anpassen von Anzeigeneinfüge-Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Anpassen von Anzeigeneinfüge-Metadaten{#customize-ad-insertion-metadata}

Sie können Anzeigeneinfüge-Metadaten anpassen.

1. Legen Sie eine Zeitüberschreitung bei Werbe-Metadaten für ungelöste Chancen fest.

   Der Standardwert für diese Zeitüberschreitung beträgt 20 Sekunden.
1. Geben Sie Folgendes ein, um den Wert auf 10 Sekunden zu ändern:

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   Die `timeout` -Eigenschaft wird in der `AdvertisingMetadata` und dieser Timeout für alle benutzerdefinierten Anzeigeneinstellungen festgelegt werden, die von der `AdvertisingMetadata` -Klasse. Wenn Benutzer beispielsweise benutzerdefinierte Einstellungen für einen FreeWheel-Resolver definieren, können sie mithilfe dieser Einstellung eine standardmäßige Zeitüberschreitung festlegen.

1. Erstellen `MediaPlayerItemConfig` mit den Anzeigeneinstellungen in Schritt 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Verwenden Sie diese Konfiguration beim Aufruf von `replaceCurrentResource` on `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```
