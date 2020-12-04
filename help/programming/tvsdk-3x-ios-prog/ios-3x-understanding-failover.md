---
description: Die Handhabung von Failover erfolgt, wenn eine variante Wiedergabeliste über mehrere Darstellungen für dieselbe Bitrate verfügt und eine der Darstellungen nicht mehr funktioniert. Das TVSDK wechselt zwischen Darstellungen.
seo-description: Die Handhabung von Failover erfolgt, wenn eine variante Wiedergabeliste über mehrere Darstellungen für dieselbe Bitrate verfügt und eine der Darstellungen nicht mehr funktioniert. Das TVSDK wechselt zwischen Darstellungen.
seo-title: Failover
title: Failover
uuid: 064886ab-afa2-4afc-b795-d094b31934b8
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---


# Failover {#failover}

Die Handhabung von Failover erfolgt, wenn eine variante Wiedergabeliste über mehrere Darstellungen für dieselbe Bitrate verfügt und eine der Darstellungen nicht mehr funktioniert. Das TVSDK wechselt zwischen Darstellungen.

Das folgende Beispiel zeigt eine Variantenplaylist mit Failover-URLs mit derselben Bitrate:

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

Wenn TVSDK die Wiedergabeliste lädt, wird eine Warteschlange erstellt, in der die URLs für alle Darstellungen des Inhalts für die gleiche Bitrate gespeichert werden. Wenn eine URL-Anforderung fehlschlägt, verwendet TVSDK die nächste URL mit derselben Bitrate aus der Failover-Warteschlange. Zu jeder bestimmten Ausfallzeit durchläuft TVSDK einmal alle verfügbaren URLs, bis eine korrekt funktioniert oder bis alle verfügbaren URLs versucht wurden. Wenn TVSDK versucht hat, alle verfügbaren URLs abzuspielen und keine der URLs funktioniert, beendet TVSDK die Wiedergabe des Inhalts.

Failover tritt nur auf M3U8-Ebene auf, d. h.:

* Bei VOD kann ein Failover nur dann erfolgen, wenn versucht wird, die Wiedergabe zu starten, und nicht, nachdem die Wiedergabe gestartet wurde.
* Beim Live-Streaming kann ein Failover in der Mitte des Streams stattfinden.

>[!TIP]
>
>TVSDK bietet anstelle des Apple AV Foundation-Players eine Failover-Behandlung.