---
description: Es wurden neue APIs eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren.
title: Offline-Wiedergabe mit Android
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Offline-Wiedergabe mit Android {#offline-playback-with-android}

Die folgenden APIs wurden eingeführt, die TVSDK anweisen, den Netzwerkkonnektivitätsstatus beim Herunterladen von Manifesten zu ignorieren. Der Netzwerkkonnektivitätsstatus wird im Allgemeinen beim adaptiven Bitrate-Streaming (ABR) verwendet, um zu bestimmen, ob ein Ausweichversuch unternommen werden soll oder darauf gewartet werden soll, dass das Netzwerk wieder aufgenommen wird.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

Sie können diese Einstellung aktivieren und die Netzwerkverbindung ignorieren.

Satz `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` auf &quot;true&quot;. Der Standardwert für einen booleschen Wert ist &quot;false&quot;.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
