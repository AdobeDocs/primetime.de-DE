---
title: Bootstrap-API
description: 'Bootstrap-API '
translation-type: tm+mt
source-git-commit: bf99c76bbbb67560adc675cf84297b8d3b04e19d
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---


# Bootstrap-API {#bootstrap-api}

Die Bootstrap-API ist in der Regel die URL, die an die Client/Video-Wiedergabe-APIs gesendet wird.  Informationen zu den konfigurierbaren Optionen und Parametern finden Sie unter [Bootstrap-API-Parameter](#bootstrap-api-parameters).

## Befehl an den Manifestserver {#send-a-command-to-the-manifest-server} senden

1. Senden Sie eine `HTTP GET`-Anforderung für eine Bootstrap-URL, die mit dem folgenden Muster erstellt wurde:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **File** extensionDefined. `.m3u8` wenn das Zielgruppen-Manifest HLS ist,  `.mpd` wenn sich die Zielgruppen im DASH befinden.

   * **** PublisherAssetIDR erforderlich. Die eindeutige ID des Herausgebers für den jeweiligen Inhalt.

   * **Content** URLR erforderlich. URL der M3U8-Inhaltsdatei, Base64-kodiert, um innerhalb der Manifestserver-URL sicher zu sein. Die Inhalts-URL muss auf eine Variante der M3U8-Datei verweisen, auch wenn es nur einen Bitratenstream gibt.

   * **Abfrage** ParameterDiese stellen den unterschiedlichsten Teil der Anforderung dar. Sie teilen dem Manifestserver mit, welcher Client die Anforderung ausführt und was der Manifestserver tun soll.

   Beispiel:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- oder HTTPS-Anforderungen**

   Der Manifestserver erstellt URLs mit demselben HTTP-Protokoll wie die Clientanforderung. Wenn ein Player eine nicht sichere HTTP-Anforderung (HTTP) sendet, gibt der Manifestserver Manifest-URLs und Auditude-Verfolgungs-URLs mit dem HTTP-Protokoll zurück. Wenn ein Player eine sichere HTTP-Verbindung (HTTPS), einen Manifestserver, herstellt, gibt er Manifest-URLs und Auditude-Tracking-URLs mit dem HTTPS-Protokoll zurück.

   >[!NOTE]
   >
   >Der Manifestserver kann das Protokoll (HTTP oder HTTPS) von Tracking-Beacons von Drittanbietern nicht ändern. Sie müssen sich an die Inhalts- und Drittanbieter für Werbeanzeigen wenden, damit diese die gewünschten Protokolle konfigurieren können.  Die Segmente-URL-Protokolle können geändert werden. Verwenden Sie jedoch standardmäßig dieselben Protokolle, die in den Zielgruppen-Manifests definiert sind.

## Bootstrap-API-Parameter {#bootstrap-api-parameters}

Die Parameter für die Abfrage geben dem Manifestserver an, welche Art von Client die Anforderung gesendet hat und was dieser Client vom Manifestserver tun möchte. Einige sind erforderlich, andere weisen bestimmte akzeptable Formate oder Werte auf.
Die vollständige URL besteht aus der Basis-URL, gefolgt von einem Fragezeichen und anschließend `parameterName=value` durch ein kaufmännisches Und getrennten Argumenten. Beispiel, `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

Der Manifestserver erkennt die folgenden Parameter. Alle Abfragezeichenfolgen\
werden an den Anzeigen-Server übergeben.

| parameter | description | formate |
|---|---|---|
| _sid_ | Eine eindeutige ID, die vom Manifestserver zum Generieren der Sitzungs-ID verwendet wird. | Erforderlich für beide DASH/HLS |
| live | Benachrichtigt Primetime-Ad Insertion, dass das übergebene Inhaltselement ein Live-Stream ist.  Wenn dieser Parameter nicht übergeben wird, stellt Primetime Ad-Einfügung eine sekundäre Anforderung beim anfänglichen Manifestaufruf dar, um zu ermitteln, ob das Manifest live oder vod ist.<br>Mögliche Werte:<br>true für live <br>contentfalse für vod <br>contentomit zur automatischen Erkennung | Optional für HLS.  Erforderlich für DASH |
| z | Die Zonen-ID für das Asset, das Primetime Ad Insertion bereitgestellt werden muss. Wird von Ihrem technischen Kundenbetreuer für Adobe bereitgestellt. | Erforderlich für beide DASH/HLS |
| Pabimode | Aktiviert [Teilweise Einfügen von Werbeunterbrechungen](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) für Live-Streams.<br>Mögliche Werte:<br>true, um die Deaktivierung zu <br>aktivieren (Standard deaktiviert) | HLS/DASH |
| ptadtimeout | Ermöglicht die Begrenzung der gesamten Anzeigenauflösungszeit, wenn die Reaktion der nachgeschalteten Anbieter zu lange dauert.  Langsam ausgeführte Antworten können zu Wiedergabeproblemen führen. Auf diese Weise kann Primetime DAI eine Antwort innerhalb einer bestimmten Frist erzwingen.<br>Mögliche Werte:<br>numerische Zeichenfolge in Millisekunden.<br>Deaktivieren auslassen (Standard deaktiviert) | HLS/DASH |
| ptadwindow | Dauer (in Sekunden) des Lookback-Anzeigenentscheidungsfensters - wie lange Primetime Ad Insertion nach Anzeigen-Hinweisen sucht, wenn ein DVR-Benutzer dem Stream beitritt. Bei einem Wert von null wird die Entscheidung für die Anzeige im anfänglichen Manifest deaktiviert, wobei die Entscheidung erst nach der ersten Aktualisierung fortgesetzt wird. Dieser Parameter ist nützlich, um das Einfügen von Anzeigen in Sitzungen zu deaktivieren, die nur einige Sekunden dauern können (z. B. das Spiegeln von Kanälen).<br>Mögliche Werte:<br>numerische Zeichenfolge 0-1800 (Standard 1800) | Nur HLS |
| ptassetid | Eindeutige ID des Inhalts, der vom Herausgeber zugewiesen und gepflegt wird.  Erforderlich, wenn sie zusammen mit dem Akamai Ad Scaler verwendet werden. | HLS/DASH |
| ptcdn | Liste eines oder mehrerer CDNs zum Hosten transkodierter Assets. Weitere Informationen finden Sie unter [Versand und Datenspeicherung](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md).<br>Mögliche Werte:<br>akamai, level3, llnw (limelight-Netzwerke), comcast.<br>Standardmäßig werden Primetime-Ad Insertion-CDNs verwendet. | HLS/DASH |
| ptcueformat | Das angegebene Format der Tags, die für die Anzeigenentscheidung verwendet werden sollen (z. B. Scte35).<br>Mögliche Werte:<br>dpisimple, dpiscte35, <br>elementalWenden Sie sich bei benutzerdefinierten Cue-Formaten an Ihren Kundenbetreuer, um den Wert für Ihren Anwendungsfall zu ermitteln | HLS/DASH |
| ptfailover | Weist den Manifestserver an, Primär- und Failover-Streams zu identifizieren, die in der Übergeordnet-Wiedergabeliste angegeben sind, und sie als Trennsätze zu behandeln. Dies erleichtert Ausfallsicherung und verhindert Zeitfehler. (Nur für Apple HLS-Geräte.) Weitere Informationen finden Sie unter [Erleichterung des Umstiegs des HLS-Players](hls-switching-to-failover.md) | Nur HLS |
| ptmulticall | Wenn diese Option aktiviert ist, wird für jeden Wert in einem VOD-Asset eine separate Anzeigenanforderung gesendet.  Primetime Ad Insertion versucht standardmäßig, alle verfügbaren Informationen zu erfassen und sie in einer Anforderung an den Anzeigen-Server zu senden. Mögliche Werte:true zur Aktivierung, <br>Deaktivieren auslassen (Standard deaktiviert) | HLS/DASH |
| ptparallelstream | Ermöglicht Kunden mit Playern, die parallel CMAF-demuxed Audio- oder Videostreams anfordern, um sicherzustellen, dass Anzeigen in Audio- und Videospuren konsistent sind. | Nur HLS |
| ptprotoswitch | Aktiviert benannte Regeln zum erneuten Schreiben von Manifesten und Regeln zum Abrufen von Anzeigen, die normalerweise von Ihrem Kundenbetreuer eingerichtet werden.<br>Beispiel: adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | Aktiviert die Injektion von EXT-X-DISCONTINUITY-SEQUENCE-Tags in HLS-Header.Mögliche Werte:true, um die Deaktivierung zu aktivieren (Standard deaktiviert) | Nur HLS |
| pttimeline | Eine Zeichenfolge, die die gewünschte Zeitschiene für Anzeigenplatzierung und -inhalt enthält, wodurch Werbeunterbrechungen im Inhaltsstream überschrieben werden. [ Siehe VOD-Timeline-Format  ] | HLS/DASH |
| pttoken | Aktiviert Schutzmechanismen für Inhaltsfragmente/Segmentautorisierungstoken für CDNs<br>Mögliche Werte:<br>akamai, llnw (limelight), ctl (centurylink) (Standard-Tokenisierung ist deaktiviert) | HLS/DASH |
| pttrackingmode | Aktivieren Sie Anzeigenverfolgungssysteme.<br>Mögliche Werte:<br>Einfach für clientseitige Anzeigenverfolgung <br>für serverseitige Anzeigenverfolgung <br>miteinfachem Tracking für hybride Client/Server-Anzeigenverfolgung (standardmäßig wird keine Anzeigenverfolgung durchgeführt) | HLS/DASH |
| pttrackingposition | Weist den Manifestserver an, nur Anzeigenverfolgungsinformationen zurückzugeben. Geben Sie diesen Parameter nicht in der Bootstrap-Anforderung an.<br>Hinweis: Der Manifestserver ignoriert alle übergebenen Werte. Wenn Sie jedoch eine Null- oder leere Zeichenfolge übergeben, gibt der Manifestserver das M3U8 zurück | HLS/DASH<br>Clientseitige Verfolgung |
| pttrackingversion | Legt die Formatversion fest, die zurückgegeben werden soll.<br>Mögliche Werte:<br>v1, v2, v3 oder vmap | HLS/DASH<br>Clientseitige Verfolgung |
| scteTracking | Dieser Parameter gibt dem Manifestserver an, dass der Player, der das M3U8 abruft, SCTE-Tag-Informationen abrufen muss.<br>Mögliche Werte:<br>true oder false (Standard false)<br>Hinweis: Die SCTE-35-Daten werden im JSON-Sidecar mit der folgenden Kombination von Abfrage-Parameterwerten zurückgegeben:<br>ptcueformat=turner | elementar | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | Nur HLS |
| vetargetmultiplier | Die Anzahl der Segmente vom Live-Point Der Pre-Roll-Offset wird wie folgt konfiguriert: ( vetargetmultiplier * targetduration ) + vebufferlength<br>Hinweis: Dieser Parameter gilt nur für Live/Lineare HLS-Streams<br>Mögliche Werte:<br>Numerische Float<br>(Standard: 3.0 - entspricht der HLS-Spezifikation) | Nur HLS |
| vebufferLength | Die Anzahl der Sekunden ab dem Livepunkt, die in Verbindung mit dem vetargetmultiplier verwendet wird.<br>Hinweis: Dieser Parameter gilt <br>nur für Live/Lineare HLS-StreamsMögliche Werte:<br>Numerischer Float<br>(Standard: 3.0) | Nur HLS |
