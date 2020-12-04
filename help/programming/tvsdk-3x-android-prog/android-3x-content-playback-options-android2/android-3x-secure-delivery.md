---
description: TVSDK führt sicheren Versand über HTTPS ein.
seo-description: TVSDK führt sicheren Versand über HTTPS ein.
seo-title: Sicherer Versand über HTTPS
title: Sicherer Versand über HTTPS
translation-type: tm+mt
source-git-commit: 4a2271fc481b37bb0a437091de6efe98fcb348d9
workflow-type: tm+mt
source-wordcount: '91'
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
