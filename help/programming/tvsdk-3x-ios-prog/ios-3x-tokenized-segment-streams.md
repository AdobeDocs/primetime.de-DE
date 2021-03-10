---
description: HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.
title: Tokenisierte Segmentströme
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Tokenisierte Segmentströme {#tokenized-segment-streams}

HLS-Streams, die über ein Content Versand Network (CDN) bereitgestellt werden, können manchmal Authentifizierungstoken für die Manifestanforderungen und Segmentanforderungen zur Überprüfung verwenden. Diese Token können als URL-Parameter oder als Cookie-Kopfzeilen bereitgestellt werden.

Tokens, die als Cookies in der Antwort auf das Übergeordnet-Manifest (m3u8) bereitgestellt werden, werden nicht für Segmentanforderungen freigegeben, selbst wenn die Segmentanforderungen für dieselbe Domäne gelten. Um die Freigabe dieser Cookies in einer Segmentanforderung zu aktivieren, legen Sie die folgende Eigenschaft auf der `PTMetadata`-Instanz fest, die dem Player-Element bereitgestellt wird: 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

Eine zusätzliche Anforderung wird an das Übergeordnet-Manifest (m3u8) gesendet, bevor die Wiedergabe des Streams beginnt.

>[!IMPORTANT]
>
>Diese Funktion zum Teilen von Cookies wird nur auf Geräten mit iOS 8 oder höher unterstützt.

