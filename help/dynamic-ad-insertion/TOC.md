---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Primetime Dynamic Ad Insertion-Hilfe
user-guide-description: Explains how to monetize content by inserting user-targeted dynamic ads on the server and engage audience with personalized ads.
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Dynamische Ad Insertion-Hilfe {#ad-insertion}

+ [Übersicht über dynamische Ad Insertion](home.md)
+ Erste Schritte mit Primetime Ad Insertion{#get-started}
   + [Übersicht](get-started-ptai.md)
   + [Vorbereiten der Verwendung von Primetime Ad Insertion](setup-ptai.md)
   + [Anzeigen-Server integrieren](integrate-ad-server.md)
   + [CDN integrieren](integrate-cdn.md)
   + [Verwenden Sie die Anzeigeneinfügung in Live-/Linear-Streams](ad-insertion-live-linear-stream.md)
   + [Verwendung der Anzeigeneinfügung für VOD](ad-insertion-vod.md)
   + [Einrichten der Anzeigenverfolgung](set-up-ad-tracking.md)
+ [Versionshinweise zur dynamischen Ad Insertion](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [Manifestserver-Debugging-Tool](manifest-server-debugging-tool.md)

<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ Manifestserver-API für Ad Insertion {#manifest-server}
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
