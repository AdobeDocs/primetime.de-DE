---
description: HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.
seo-description: HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.
seo-title: Tokenisierte Segmentströme
title: Tokenisierte Segmentströme
uuid: b17bb5bc-2029-4113-ac44-b1d30aa08ca6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Tokenisierte Segmentströme{#tokenized-segment-streams}

HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.

Tokens, die als Cookies in der Antwort des Master-Manifests (m3u8) bereitgestellt werden, werden nicht für die (ts) Segmentanforderungen freigegeben, auch wenn die Segmentanforderungen für dieselbe Domäne gelten. Um die Freigabe dieser Cookies in einer Segmentanforderung zu aktivieren, legen Sie die folgende Eigenschaft in der dem Player-Element bereitgestellten `PTMetadata` Instanz fest:

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Eine zusätzliche Anforderung wird an das Master-Manifest (m3u8) gesendet, bevor die Wiedergabe des Streams beginnt.

>[!IMPORTANT]
>
>Diese Funktion zum Teilen von Cookies wird nur auf Geräten mit iOS 8 oder höher unterstützt.

