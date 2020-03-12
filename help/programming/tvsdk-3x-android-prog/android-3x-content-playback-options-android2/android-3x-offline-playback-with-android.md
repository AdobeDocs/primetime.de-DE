---
description: 'Es wurden neue APIs eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. '
seo-description: 'Es wurden neue APIs eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. '
seo-title: Offline-Wiedergabe mit Android
title: Offline-Wiedergabe mit Android
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Offline-Wiedergabe mit Android {#offline-playback-with-android}

Die folgenden APIs wurden eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. Der Netzwerkkonnektivitätsstatus wird im Allgemeinen während des adaptiven Bitrate-Streaming (ABR) verwendet, um zu bestimmen, ob ein Ausweichversuch durchgeführt oder auf die Wiederaufnahme des Netzwerks gewartet werden soll.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

Sie können diese Einstellung aktivieren und die Netzwerkverbindung ignorieren.

Auf `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` &quot;true&quot;setzen. Der Standardwert für einen booleschen Wert ist false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
