---
description: HLS-Streams, die über ein Content Delivery Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für Manifest- und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.
title: Tokenisierte Segmentströme
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Tokenisierte Segmentströme {#tokenized-segment-streams}

HLS-Streams, die über ein Content Delivery Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für Manifest- und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.

Token, die als Cookies in der Master-Manifestantwort (m3u8) bereitgestellt werden, werden nicht für die Segmentanforderungen (ts) freigegeben, selbst wenn die Segmentanforderungen für dieselbe Domäne gelten. Um die Freigabe dieser Cookies in einer Segmentanfrage zu aktivieren, legen Sie die folgende Eigenschaft auf der `PTMetadata` Instanz, die dem Player-Element bereitgestellt wird: 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Eine zusätzliche Anfrage wird an das Master-Manifest (m3u8) gesendet, bevor die Wiedergabe des Streams beginnt.

>[!IMPORTANT]
>
>Diese Cookie-Sharing-Funktion wird nur auf Geräten mit iOS 8 oder höher unterstützt.
