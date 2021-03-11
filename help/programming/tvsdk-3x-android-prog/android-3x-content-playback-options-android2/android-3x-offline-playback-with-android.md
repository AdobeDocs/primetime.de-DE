---
description: 'Es wurden neue APIs eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. '
title: Offline-Wiedergabe mit Android
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# Offline-Wiedergabe mit Android {#offline-playback-with-android}

Die folgenden APIs wurden eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. Der Netzwerkkonnektivitätsstatus wird im Allgemeinen während des adaptiven Bitrate-Streaming (ABR) verwendet, um zu bestimmen, ob ein Ausweichversuch durchgeführt oder auf die Wiederaufnahme des Netzwerks gewartet werden soll.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

Sie können diese Einstellung aktivieren und die Netzwerkverbindung ignorieren.

Setzen Sie `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` auf true. Der Standardwert für einen booleschen Wert ist false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
