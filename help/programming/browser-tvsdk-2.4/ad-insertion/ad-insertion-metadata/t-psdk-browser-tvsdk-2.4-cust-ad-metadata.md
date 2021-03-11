---
description: Sie können Anzeigeneinfüge-Metadaten anpassen.
title: Anpassen von Anzeigeneinfügemetadaten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Anpassen der Anzeigeneinfügemetadaten{#customize-ad-insertion-metadata}

Sie können Anzeigeneinfüge-Metadaten anpassen.

1. Legen Sie eine Zeitüberschreitung bei Werbe-Metadaten für ungelöste Möglichkeiten fest.

   Der Standardwert für diesen Timeout ist 20 Sekunden.
1. Geben Sie Folgendes ein, um den Wert auf 10 Sekunden zu ändern:

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   Die `timeout`-Eigenschaft wird in der `AdvertisingMetadata`-Klasse definiert. Dieser Timeout kann für alle benutzerdefinierten Anzeigeneinstellungen festgelegt werden, die von der `AdvertisingMetadata`-Klasse abgeleitet werden. Wenn Benutzer beispielsweise benutzerdefinierte Einstellungen für einen FreeWheel-Auflöser definieren, können sie mithilfe dieser Einstellung einen Standard-Timeout festlegen.

1. Erstellen Sie `MediaPlayerItemConfig` mit den Anzeigeneinstellungen in Schritt 2.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. Verwenden Sie diese Konfiguration, wenn Sie `replaceCurrentResource` für `MediaPlayer` aufrufen.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

