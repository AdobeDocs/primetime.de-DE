---
description: TVSDK führt eine sichere Bereitstellung über HTTPS ein.
title: Sichere Bereitstellung über HTTPS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Sichere Bereitstellung über HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK unterstützt die HTTPS-Bereitstellung für alle Aufrufe, die von TVSDK stammen, darunter

* Auditude Ad Server-Aufrufe
* CRS-Anforderungen
* DRM-Lizenzaufrufe
* Video Analytics-Pings
* Abrechnungs-Pings

Um diese Funktion verwenden zu können, stellen Sie sicher, dass die für die Bereitstellung der oben genannten Anfragen konfigurierten Server HTTPS unterstützen.

Dieses neue Verhalten ist standardmäßig nicht aktiviert. Verwenden Sie Folgendes, um einen sicheren Versand vor dem Aufruf von zu aktivieren `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
