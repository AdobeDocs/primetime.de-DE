---
seo-title: Beispiel eines benutzerdefinierten VOD-Assets
title: Beispiel eines benutzerdefinierten VOD-Assets
uuid: 599054c3-d6ef-4f85-9a0f-39c7e4f6ab24
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# Beispiel für ein benutzerdefiniertes VOD-Asset{#example-of-a-customized-vod-asset}

Hier ein Beispiel für ein benutzerdefiniertes VOD-Asset:

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

* Eine Benachrichtigung, wenn `#EXT-X-ASSET`-Tags oder andere Gruppen von benutzerdefinierten Tag-Namen, für die Sie ein Abonnement abgeschlossen haben, in der Datei vorhanden sind.
* Fügen Sie Anzeigen ein, wenn ein `#EXT-X-AD`-Tag oder ein anderer benutzerdefinierter Tag-Name im Stream gefunden wird.

