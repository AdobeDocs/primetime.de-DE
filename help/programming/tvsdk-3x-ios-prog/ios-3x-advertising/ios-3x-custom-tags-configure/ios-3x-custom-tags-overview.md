---
seo-title: Beispiel eines benutzerdefinierten VOD-Assets
title: Beispiel eines benutzerdefinierten VOD-Assets
uuid: 23ff3778-09d4-43ef-89c3-67f8fc56f5da
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# Beispiel eines benutzerdefinierten VOD-Assets {#example-of-a-customized-vod-asset}

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

