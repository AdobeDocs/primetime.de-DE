---
description: Sie können Anzeigeneinfüge-Metadaten anpassen.
seo-description: Sie können Anzeigeneinfüge-Metadaten anpassen.
seo-title: Anpassen von Anzeigeneinfügemetadaten
title: Anpassen von Anzeigeneinfügemetadaten
uuid: 047470d3-45bd-48be-82ce-4e9d9fe6ea10
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Anpassen von Anzeigeneinfügemetadaten{#customize-ad-insertion-metadata}

Sie können Anzeigeneinfüge-Metadaten anpassen.

1. Legen Sie eine Zeitüberschreitung bei Werbe-Metadaten für ungelöste Möglichkeiten fest.

   Der Standardwert für diesen Timeout ist 20 Sekunden.
1. Geben Sie Folgendes ein, um den Wert auf 10 Sekunden zu ändern:

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   Die `timeout` Eigenschaft wird in der `AdvertisingMetadata` -Klasse definiert. Dieser Timeout kann für alle benutzerdefinierten Anzeigeneinstellungen festgelegt werden, die von der `AdvertisingMetadata` Klasse abgeleitet werden. Wenn Benutzer beispielsweise benutzerdefinierte Einstellungen für einen FreeWheel-Auflöser definieren, können sie mithilfe dieser Einstellung einen Standard-Timeout festlegen.

1. Erstellen Sie `MediaPlayerItemConfig` mit den Anzeigeneinstellungen in Schritt 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Verwenden Sie diese Konfiguration beim `replaceCurrentResource` Anrufen `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

