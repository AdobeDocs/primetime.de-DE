---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Primetime Dynamic Ad Insertion Help
translation-type: tm+mt
source-git-commit: 9d8fa7b8deffcf0d86f0c8343b11fad042d8d4df

---


# Hilfe zum Einfügen dynamischer Anzeigen {#ad-insertion}

+ [Übersicht über die dynamische Anzeigeneinfügung](home.md)
+ [Versionshinweise zur dynamischen Anzeigeneinfügung](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [Manifestserver-Debugging-Tool](manifest-server-debugging-tool.md)
<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ Manifestserver-API für Anzeigeneinfügung {#manifest-server}
   + [Übersicht über Manifest Server-Interaktionen](msapi-topics/ms-overview.md)
   + Erste Schritte mit Manifest Server {#get-started}
      + [Befehl an den Manifestserver senden](msapi-topics/ms-getting-started/ms-sending-cmd.md)
      + [Manifestserver-Abfrage](msapi-topics/ms-getting-started/ms-api-query-params.md)
   + Anzeigeneinfügeanforderungen {#ad-insert}
      + [Anfragen zum Einfügen von Werbeanzeigen](msapi-topics/ms-insert-ads/ms-ad-insert.md)
      + [Optionale Abfragen nach Client und Situation](msapi-topics/ms-insert-ads/ms-api-query-param-situation.md)
      + [Erleichterung des Umstiegs des HLS-Players auf Failover-/Backup-Streams](msapi-topics/ms-insert-ads/hls-switching-to-failover.md)
      + [Mehrere Bitratenströme](msapi-topics/ms-insert-ads/ms-api-mbr-streams.md)
      + [Einfügen eines Teilformulars mit Werbeunterbrechung](msapi-topics/ms-insert-ads/partial-ad-break-insetion.md)
      + [Mehrere CDN-Unterstützung für CRS und Versand](msapi-topics/ms-insert-ads/ms-api-multi-cdns-for-crs.md)
   + VOD-Zeitschienen ersetzen {#replace-vod}
      + [Änderungen an VOD](msapi-topics/ms-changes-vod-timeline/ms-replace-vod-timeline.md)
      + [VOD-Timeline-Format](msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)
      + [VOD-Timeline ersetzen](msapi-topics/ms-changes-vod-timeline/t-ms-replace-vod-timeline.md)
   + Verfolgung der Anzeigeneffektivität {#ad}
      + [Anzeigenverfolgung](msapi-topics/ms-at-effectiveness/ms-at-overview.md)
      + [Aktivieren der clientseitigen Anzeigenverfolgung](msapi-topics/ms-at-effectiveness/ms-enable-client-side-ad-tracking.md)
      + [Übersicht über die clientseitige Verfolgung ohne TVSDK](msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md)
      + [API für Player zur Interaktion mit dem Manifestserver](msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)
      + [EXT-X-MARKER-Richtlinie](msapi-topics/ms-at-effectiveness/ms-api-playlists.md)
   + [Cookies](msapi-topics/ms-cookies.md)
   + [Unterstützung für WebVTT-Beschriftungen](msapi-topics/ms-webvtt-captions.md)
   + Liste von Dateiformaten {#list}
      + [Dateiformate](msapi-topics/ms-list-file-formats/ms-api-file-formats.md)
      + [JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste](msapi-topics/ms-list-file-formats/ms-json-m3u8.md)
      + [JSON-Formate für die Verfolgung von URLs](msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md)
      + [VMAP-Format zur Verfolgung von URLs](msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md)
   + [Anforderungen an Videoplayer](msapi-topics/ms-player-req.md)
+ Primetime Creative Repackage Service {#crs}
   + [Übersicht über CRS](creative-repackaging-service/crs-overview.md)
   + [Hauptverwendung von CRS](creative-repackaging-service/jit-async-hls-conv.md)
   + [Multi-CDN-Unterstützung](creative-repackaging-service/multi-cdn-supportt.md)
   + [Detaillierte Workflows für JIT-Neuverpackungen](creative-repackaging-service/jit-repackage.md)
   + [Verwenden von CRS zum Einfügen von ID3-Timed-Metadaten-Tags](creative-repackaging-service/inject-id3.md)
   + [API neu packen](creative-repackaging-service/api-repackage.md)
