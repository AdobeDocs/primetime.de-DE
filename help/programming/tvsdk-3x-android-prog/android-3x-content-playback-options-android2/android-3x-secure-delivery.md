---
description: TVSDK führt sicheren Versand über HTTPS ein.
title: Sicherer Versand über HTTPS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# Sicherer Versand über HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK unterstützt HTTPS-Versand für alle Aufrufe, die von TVSDK stammen, einschließlich

* Auditude Ad Server-Aufrufe
* CRS-Anforderungen
* DRM-Lizenzanrufe
* Videoanalysen-Pings
* Rechnungspapiere

Um diese Funktion zu verwenden, stellen Sie sicher, dass die für die Bereitstellung der oben genannten Anforderungen konfigurierten Server HTTPS unterstützen.

Dieses neue Verhalten ist nicht standardmäßig aktiviert. Verwenden Sie Folgendes, um sicheren Versand vor dem Aufruf von `MediaPlayer.replaceCurrentResource()` zu aktivieren

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
