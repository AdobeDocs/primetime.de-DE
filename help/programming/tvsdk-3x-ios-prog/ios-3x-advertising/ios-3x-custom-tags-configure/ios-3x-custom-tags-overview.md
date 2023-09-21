---
title: Beispiel eines benutzerdefinierten VOD-Assets
description: Beispiel eines benutzerdefinierten VOD-Assets
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Beispiel eines benutzerdefinierten VOD-Assets {#example-of-a-customized-vod-asset}

Im Folgenden finden Sie ein Beispiel für ein benutzerdefiniertes VOD-Asset:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Ihre Anwendung könnte die folgenden Szenarien einrichten:

* Eine Benachrichtigung bei `#EXT-X-ASSET` -Tags oder andere benutzerdefinierte Tag-Namen, die Sie abonniert haben, sind in der Datei vorhanden.
* Fügen Sie Anzeigen ein, wenn eine `#EXT-X-AD` -Tag oder einen anderen benutzerdefinierten Tag-Namen finden Sie im Stream.
