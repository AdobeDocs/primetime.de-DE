---
description: Die Failover-Handhabung tritt auf, wenn eine Variantenwiedergabe mehrere Wiedergaben für dieselbe Bitrate aufweist und eine der Wiedergaben nicht mehr funktioniert. Das TVSDK wechselt zwischen Ausgabedarstellungen.
title: Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Failover {#failover}

Die Failover-Handhabung tritt auf, wenn eine Variantenwiedergabe mehrere Wiedergaben für dieselbe Bitrate aufweist und eine der Wiedergaben nicht mehr funktioniert. Das TVSDK wechselt zwischen Ausgabedarstellungen.

Das folgende Beispiel zeigt eine VariantenWiedergabeliste mit Failover-URLs mit derselben Bitrate:

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

Wenn TVSDK die Wiedergabeliste lädt, wird eine Warteschlange erstellt, in der die URLs für alle Ausgabeformate des Inhalts mit derselben Bitrate gespeichert sind. Wenn eine URL-Anforderung fehlschlägt, verwendet TVSDK die nächste URL mit derselben Bitrate aus der Failover-Warteschlange. Zu jedem bestimmten Fehlerzeitpunkt durchläuft TVSDK einmal alle verfügbaren URLs, bis es eine findet, die ordnungsgemäß funktioniert, oder bis es alle verfügbaren URLs versucht hat. Wenn TVSDK versucht hat, alle verfügbaren URLs abzuspielen und keine der URLs funktioniert, stoppt TVSDK die Wiedergabe des Inhalts.

Failover tritt nur auf M3U8-Ebene auf, d. h.:

* Bei VOD kann Failover nur auftreten, wenn es beginnt, die Wiedergabe zu versuchen, und nicht, nachdem die Wiedergabe gestartet wurde.
* Beim Live-Streaming kann Failover mitten im Stream auftreten.

>[!TIP]
>
>TVSDK bietet anstelle des Apple AV Foundation-Players eine Failover-Handhabung.
