---
description: Herausgeber können HLS-konforme Videoplayer erstellen, die mit der clientseitigen Workflows der Primetime-Manifestserver-Anzeigenverfolgung funktionieren. Die Schnittstellen zum Manifestserver für die Live-Stream- und Video-On-Demand-Fälle (VOD) unterscheiden sich geringfügig.
seo-description: Herausgeber können HLS-konforme Videoplayer erstellen, die mit der clientseitigen Workflows der Primetime-Manifestserver-Anzeigenverfolgung funktionieren. Die Schnittstellen zum Manifestserver für die Live-Stream- und Video-On-Demand-Fälle (VOD) unterscheiden sich geringfügig.
seo-title: Übersicht über die clientseitige Verfolgung ohne TVSDK
title: Übersicht über die clientseitige Verfolgung ohne TVSDK
uuid: fb23be01-3327-443d-82c4-fb0993e7fec1
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Übersicht über die clientseitige Verfolgung ohne TVSDK {#overview-of-non-tvsdk-client-side-tracking}

Herausgeber können HLS-konforme Videoplayer erstellen, die mit der clientseitigen Workflows der Primetime-Manifestserver-Anzeigenverfolgung funktionieren. Die Schnittstellen zum Manifestserver für die Live-Stream- und Video-On-Demand-Fälle (VOD) unterscheiden sich geringfügig.

Der Manifestserver stellt eine API bereit, mit der benutzerdefinierte Player die folgenden URLs anfordern können, die sie zur Berichterstellung von Ereignissen zur Anzeigenverfolgung verwenden können:

* Anzeigenimpression
* Ad-Quartil
* Fortschritt des Anzeigenpods
* Fortschritt des Inhalts-Pods

Die Manifestserver-API setzt voraus, dass jeder Videoplayer, der sie verwendet, die Mindestanforderungen erfüllt. Weitere Informationen finden Sie unter Anforderungen für [Videoplayer](../../msapi-topics/ms-player-req.md) .

## Arbeitsablauf für clientseitige Verfolgung {#section_cst_flow}

![](assets/pt_ssai_notvsdk_csat_ai-workflow.png)

1. Der Player ruft eine Manifestserver-URL vom Herausgeber ab.
1. Der Player hängt spezifische Parameter zur Abfrage an die jeweiligen Anzeigeneinfügeanforderungen an und sendet eine HTTP GET-Anforderung an die resultierende Bootstrap-URL. Die Bootstrap-URL hat folgende Syntax:

   ```
   http{s}://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{urlSafeBase64({Content URL})}.m3u8?{query parameters}
   
   For example:
   https://manifest.auditude.com/auditude/variant/
   7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.m3u8?
   u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2&__sid__=docExample02
   ```

   Die URL enthält die unter Befehl an den Manifestserver [senden beschriebenen Elemente](../../msapi-topics/ms-getting-started/ms-sending-cmd.md).

1. Der Manifestserver richtet eine Sitzung für diesen Player ein und generiert eine eindeutige Sitzungs-ID. Es wird eine neue Variante der M3U8-Wiedergabelisten-URL erstellt, die als JSON-Antwort an den Player zurückgegeben wird. JSON hat folgende Syntax:

   ```
   {
    "Master-M3U8": "https://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{SessionID}/
       {urlSafeBase64(content URL)}.m3u8?u={Asset ID}&z={Zone ID}&pttrackingmode=simple&pttrackingversion=v2
       &{Any other query parameters}"
   }
   
   For example:
   https://pcor3.manifest.auditude.com/auditude/variant/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Der Player verwendet die URL der JSON-Antwort, um die neue Variante M3U8 Master-Playlist vom Manifestserver anzufordern.
1. Der Manifestserver gibt eine neue Variante M3U8 zurück, die URLs auf Stream-Ebene mit einer ähnlichen Syntax wie die folgende enthält:

   ```
   http{s}://{manifest-server:port}/auditude/{live|vod}/{PublisherAssetID}/
     {rendition}/{groupID}/{urlSafeBase64(bit rate stream URL)}.m3u8?u={Ad Request Id}&z={Ad Zone Id}&{Any other query parameters}
   
   For example:
   #EXTM3U
   #EXT-X-VERSION:5
   #EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,DEFAULT=YES,FORCED=NO,LANGUAGE="eng",URI="https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/webvtt/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvd2VidnR0L1RPUy1lbjIubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2"
   #EXT-X-STREAM-INF:BANDWIDTH=10000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/10000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTAwMDAvdG9jXzEwMDAwLm0zdTg.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=1300000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/1300/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTMwMC90b2NfMTMwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=3400000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/3400/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMzQwMC90b2NfMzQwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=2100000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/2100/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMjEwMC90b2NfMjEwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=800000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/800/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvODAwL3RvY184MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=5000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/5000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwMC90b2NfNTAwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=7500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/7500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNzUwMC90b2NfNzUwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Der Player wählt die entsprechende URL des Manifests auf Stream-Ebene für die Wiedergabe des angehefteten Inhalts aus. Beispiel:

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. Der Manifestserver gibt ein Manifest auf Stream-Ebene zurück, das Links zu den Links zum Inhalt und zu den Segmentverknüpfungen auf Anzeigen-TS enthält. Beispiel:

   ```
      #EXTM3U
   #EXT-X-VERSION:3
   #EXT-X-TARGETDURATION:8
   #EXT-X-PLAYLIST-TYPE:VOD
   
   #EXT-X-DISCONTINUITY
   #EXTINF:8,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00001.ts
   #EXTINF:7,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00002.ts
   
   #EXT-X-DISCONTINUITY
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.0.ts
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.4000.ts
   #EXTINF:4.833,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.8000.ts   
   ```

   >[!NOTE]
   >
   >Der Player wählt die URL der Wiedergabeliste auf Streamebene aus, um den Inhaltsstream abzurufen. Der Manifestserver ruft die ursprüngliche Wiedergabeliste aus dem CDN ab. Einige Kodierer können zusätzliche Details in das `#EXTINF` Titelattribut einfügen, z. B.:
   >
   >
   ```
   >#EXTINF:6.006,LTC=2017-08-23T13:25:47+00:00
   >```

   Da der Manifestserver nicht die Bedeutung von Nicht-Standardattributen ableiten kann, um sie für eine anzeigengegeführte Wiedergabeliste zu ändern, entfernt der Manifestserver alle weiteren Attribute, die über die in diesem Tag angegebenen Daten zur Dauer hinausgehen. Weitere Informationen finden Sie im [EXTINF](https://tools.ietf.org/html/rfc8216#section-4.3.2.1) -Eintrag in der HLS-Spezifikation.


1. Um Verfolgungsinformationen anzufordern, hängt der Player den Parameter &quot;Abfrage&quot; `pttrackingposition` mit einem beliebigen alphanumerischen Wert an die URL der Wiedergabeliste auf Streamebene für die ausgewählte Bitrate an. Beispiel:

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d
   &z=173475&pttrackingmode=simple&pttrackingversion=v2&pttrackingposition=1
   ```

1. Der Manifestserver gibt die Wiedergabelistendatei zurück, die entweder mit einem [JSON](../../msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md) - oder [VMAP](../../msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md) -Objekt gefüllt ist, das die Anzeigenverfolgungsdaten für die aktuell angeforderte m3u8-Datei auf Stream-Ebene enthält.

   >[!NOTE]
   >
   >Der Manifestserver generiert nur dann Anzeigenverfolgungsobjekte, wenn in die aktuell angeforderte Wiedergabeliste auf Stream-Ebene Anzeigen eingefügt wurden. Wenn der Player eine Wiedergabeliste wiedergibt, die keine eingefügten Anzeigen enthält, gibt der Manifestserver einen HTTP-Status 201 für die Anfrage zur Anzeigenverfolgung der Wiedergabeliste zurück. Wenn der Player die Anzeigenverfolgungsanforderung für einen Stream durchführt, der nicht wiedergegeben wird, gibt der Manifestserver einen HTTP-Status 500 zurück. Wenn die aktuelle Wiedergabeanforderung z. B. für 500.m3u8 lautet, gibt der Manifestserver für die Anzeigenverfolgungsanforderung ein JSON|VMAP in 500.m3u8 zurück. Wenn der Player anschließend jedoch Streams wechselt, um den 800.m3u8 abzuspielen, werden die Anzeigenverfolgungsinformationen im 500.m3u8 ungültig, was zu einem 404-Fehler führt.

   >[!NOTE]
   >
   >Der Manifestserver generiert das Anzeigenverfolgungsobjekt basierend auf dem `pttrackingversion` Wert in der Bootstrap-URL. Wenn der Wert weggelassen `pttrackingversion` wird oder einen ungültigen Wert aufweist, füllt der Manifestserver automatisch die Anzeigenverfolgungsinformationen in den `#EXT-X-MARKER` Tags in jeder angeforderten Wiedergabeliste auf Stream-Ebene. Weitere Informationen finden Sie [unter](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md).

1. Der Player fordert jede Anzeigen-Tracking-URL für jedes Ereignis zur richtigen Zeit an.

>[!NOTE]
>
>Bei Live-Streams muss der Player die Schritte 6 bis 10 wiederholen, da der Packager die Wiedergabeliste während der gesamten Laufzeit des Live-Ereignisses ständig aktualisiert.

Während der Wiedergabe des Videos muss der Player die Abspielposition verfolgen und diese Position zusammen mit den Verfolgungs-URLs verwenden, die er von Primetime-Anzeigen erhalten hat. Die Tracking-URLs werden nach Zeitversatz vom Anfang der Wiedergabe gruppiert. Für jeden Zeitversatz gibt es eine URL für jedes Anzeigensystem, an das Verfolgungsinformationen gesendet werden sollen. Weitere Details des Formats unterscheiden sich zwischen Live-Video und Video bei Bedarf.
