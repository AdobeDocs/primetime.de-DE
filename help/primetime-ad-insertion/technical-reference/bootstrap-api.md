---
title: Bootstrap-API
description: Bootstrap-API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# Bootstrap-API {#bootstrap-api}

Die Bootstrap-API ist normalerweise die URL, die an die Client/Video-Wiedergabe-APIs gesendet wird.  Informationen zu den konfigurierbaren Optionen und Parametern finden Sie im Abschnitt [Bootstrap-API-Parameter](#bootstrap-api-parameters).

## Senden eines Befehls an den Manifestserver {#send-a-command-to-the-manifest-server}

1. Senden Sie eine `HTTP GET` Anforderung einer Bootstrap-URL, die mit dem folgenden Muster erstellt wurde:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **Dateierweiterung** Definiert. `.m3u8` wenn das Zielmanifest HLS ist, `.mpd` wenn sich die Zielmanifeste im DASH befinden.

   * **PublisherAssetID** Erforderlich. Eindeutige Kennung des Herausgebers für den jeweiligen Inhalt.

   * **Inhalts-URL** Erforderlich. URL der M3U8-Inhaltsdatei, Base64-kodiert, um sicher in der Manifestserver-URL zu sein. Die Inhalts-URL muss auf eine M3U8-Variantendatei verweisen, auch wenn es nur einen Bitratenstream gibt.

   * **Abfrageparameter** Diese stellen den unterschiedlichsten Teil des Antrags dar. Sie teilen dem Manifestserver mit, welcher Client die Anfrage stellt und was der Manifestserver tun soll.

   Beispiel:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- vs. HTTPS-Anforderungen**

   Der Manifestserver erstellt URLs mit demselben HTTP-Protokoll wie die Clientanforderung. Wenn ein Player eine nicht sichere HTTP-Anforderung (HTTP) sendet, gibt der Manifestserver Manifest-URLs und Auditude-Tracking-URLs mit dem HTTP-Protokoll zurück. Wenn ein Player eine sichere HTTP-Verbindung (HTTPS), einen Manifestserver, herstellt, werden Manifest-URLs und Auditude-Tracking-URLs mit dem HTTPS-Protokoll zurückgegeben.

   >[!NOTE]
   >
   >Der Manifestserver kann das Protokoll (HTTP oder HTTPS) der Tracking-Beacons von Drittanbietern nicht ändern. Wenden Sie sich an den Inhalt und an Drittanbieter, damit diese die gewünschten Protokolle konfigurieren können.  Die Segmente-URL-Protokolle können jedoch standardmäßig mit den in den Zielmanifesten definierten Protokollen geändert werden.

## Bootstrap-API-Parameter {#bootstrap-api-parameters}

Abfrageparameter teilen dem Manifestserver mit, welche Art von Client die Anfrage gesendet hat und was dieser Client vom Manifestserver tun möchte. Einige sind erforderlich, andere weisen bestimmte akzeptable Formate oder Werte auf.
Die vollständige URL besteht aus der Basis-URL, gefolgt von einem Fragezeichen, und `parameterName=value` durch kaufmännische Und-Zeichen getrennt. Beispiel: `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

Der Manifestserver erkennt die folgenden Parameter. Alle Abfragezeichenfolgen\
-Parameter an den Anzeigenserver übergeben werden.

| parameter | description | Formate |
|---|---|---|
| _sid_ | Eine eindeutige ID, die der Manifestserver zum Generieren der Sitzungs-ID verwendet. | Erforderlich für beide DASH/HLS |
| live | Benachrichtigt Primetime-Ad Insertion darüber, dass das übergebene Inhaltselement ein Live-Stream ist.  Wenn dieser Parameter nicht übergeben wird, sendet das Primetime-Anzeigeneinfüge eine sekundäre Anfrage beim ersten Manifestaufruf, um zu ermitteln, ob das Manifest live oder vod ist.<br>Mögliche Werte:<br>true für Live-Inhalt<br>false für vod-Inhalt<br>Unterlassen der automatischen Erkennung | Optional für HLS.  Erforderlich für DASH |
| z | Die Zone-ID für das Asset, die Primetime Ad Insertion bereitgestellt werden muss. Wird von Ihrem Adobe Technical Account Manager bereitgestellt. | Erforderlich für beide DASH/HLS |
| pabimode | Aktiviert [Teilweise-Werbeunterbrechung](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) für Live-Streams.<br>Mögliche Werte:<br>true zum Aktivieren<br>Nicht deaktivieren (Standard deaktiviert) | HLS/DASH |
| ptadtimeout | Ermöglicht die Begrenzung der gesamten Zeit für die Anzeigenauflösung, wenn die Reaktion der nachgelagerten Anbieter zu lange dauert.  Langwierige Antworten können Probleme bei der Wiedergabe verursachen. Dadurch kann Primetime DAI eine Antwort innerhalb einer bestimmten Frist erzwingen.<br>Mögliche Werte:<br>numerische Zeichenfolge in Millisekunden.<br>Nicht deaktivieren (Standard deaktiviert) | HLS/DASH |
| ptadwindow | Dauer (in Sekunden) des Lookback-Anzeigenentscheidungs-Fensters - wie weit Primetime-Ad Insertion nach AnzeigenHinweisen sucht, wenn ein DVR-Benutzer dem Stream beitritt. Bei einem Wert von null wird die Entscheidungsfindung für Mid-Roll-Anzeigen im anfänglichen Manifest deaktiviert, wobei die Entscheidung erst nach der ersten Aktualisierung fortgesetzt wird. Dieser Parameter ist nützlich, um das Einfügen von Anzeigen in Sitzungen zu deaktivieren, die nur einige Sekunden dauern können (auch Kanalflipping genannt).<br>Mögliche Werte:<br>numerische Zeichenfolge 0-1800 (Standard 1800) | Nur HLS |
| ptassetid | Eindeutige ID des Inhalts, der vom Herausgeber zugewiesen und gepflegt wird.  Erforderlich bei Verwendung in Verbindung mit Akamai Ad Scaler. | HLS/DASH |
| ptcdn | Liste eines oder mehrerer CDNs, die transkodierte Assets hosten sollen. Weitere Informationen finden Sie unter [Versand und Speicherung](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md).<br>Mögliche Werte:<br>akamai, level3, llnw (limelight Networks), comcast.<br>Standardmäßig werden Primetime-Ad Insertion-CDNs verwendet. | HLS/DASH |
| ptcueformat | Das angegebene Format von Tags, die für Anzeigenentscheidungen verwendet werden sollen (z. B. screen35).<br>Mögliche Werte:<br>dpisimple, dpiscte35, elemental<br>Wenden Sie sich bei benutzerdefinierten Cue-Formaten an Ihren technischen Kundenbetreuer, um den für Ihren Anwendungsfall zu verwendenden Wert zu erhalten. | HLS/DASH |
| ptfailover | Signalisiert den Manifestserver, primäre und Failover-Streams zu identifizieren, die in der Master-Wiedergabeliste angegeben sind, und sie als getrennte Sets zu behandeln. Dies erleichtert das Failover und verhindert Timing-Fehler. (Nur für Apple HLS-Geräte.) Weitere Informationen finden Sie unter [HLS-Player-Switching erleichtern](hls-switching-to-failover.md) | Nur HLS |
| ptmulticall | Wenn diese Option aktiviert ist, wird für jeden in einem VOD-Asset gefundenen Wert eine separate Anzeigenanforderung gesendet.  Standardmäßig versucht Primetime Ad Insertion, alle verfügbaren Informationen zu sammeln und in einer Anfrage an den Adserver zu senden. Mögliche Werte:true zur Aktivierung, <br>Nicht deaktivieren (Standard deaktiviert) | HLS/DASH |
| ptparallelstream | Ermöglicht Kunden mit Playern, die parallel CMAF-demuxed Audio- oder Videostreams anfordern, um sicherzustellen, dass Anzeigen in Audio- und Videospuren konsistent sind. | Nur HLS |
| ptprotoswitch | Aktiviert benannte Manifest-Neuschreibungsregeln und Anzeigenabrufregeln, die normalerweise von Ihrem technischen Support-Mitarbeiter eingerichtet werden.<br>Beispiel: adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | Aktiviert die Injektion von EXT-X-DISCONTINUITY-SEQUENCE-Tags in HLS-Kopfzeilen.Mögliche Werte:true , um die Deaktivierung zu ermöglichen (Standard deaktiviert) | Nur HLS |
| pttimeline | Eine Zeichenfolge, die die gewünschte Timeline für die Anzeigenplatzierung und den Inhalt enthält, wodurch Werbeunterbrechungen im Inhaltsstream überschrieben werden. [Siehe VOD-Timeline-Format] | HLS/DASH |
| pttoken | Aktiviert Schutzmechanismen für Inhaltsfragmente/Segmentautorisierungstoken für CDNs<br>Mögliche Werte:<br>akamai, llnw (limelight), ctl (centurylink) (Standard-Tokenisierung ist deaktiviert) | HLS/DASH |
| pttrackingmode | Aktivieren Sie Anzeigen-Tracking-Systeme.<br>Mögliche Werte:<br>einfach für die clientseitige Anzeigenverfolgung<br>SMS für serverseitige Anzeigenverfolgung<br>simplesstm für das hybride Client-/Server-Anzeigen-Tracking (standardmäßig wird kein Anzeigen-Tracking durchgeführt) | HLS/DASH |
| pttrackingposition | Weist den Manifestserver an, nur Anzeigenverfolgungsinformationen zurückzugeben. Geben Sie diesen Parameter nicht in der Bootstrap-Anfrage an.<br>Hinweis: Der Manifestserver ignoriert alle übergebenen Werte. Wenn Sie jedoch eine Null- oder leere Zeichenfolge übergeben, gibt der Manifestserver das M3U8 zurück | HLS/DASH<br>Clientseitige Verfolgung |
| pttrackingversion | Legt die Formatversion fest, die zurückgegeben werden soll.<br>Mögliche Werte:<br>v1, v2, v3 oder vmap | HLS/DASH<br>Clientseitige Verfolgung |
| screenTracking | Dieser Parameter gibt dem Manifestserver an, dass der Player, der das M3U8 abruft, SCTE-Tag-Informationen benötigt, um abgerufen zu werden.<br>Mögliche Werte:<br>true oder false (Standard false)<br>Hinweis: Die SCTE-35-Daten werden im JSON-Sidecar mit der folgenden Kombination von Abfrageparameterwerten zurückgegeben:<br>ptcueformat=turner | elementar | nfl | DPIScte35<br>pttrackingversion=v2<br>screenTracking=true<br> | Nur HLS |
| vetargetmultiplikator | Die Anzahl der Segmente vom Live-Point Der Pre-Roll-Versatz wird wie folgt konfiguriert: ( vetargetmultiplier * targetduration ) + vebufferlength<br>Hinweis: Dieser Parameter gilt nur für Live-/Linear-HLS-Streams<br>Mögliche Werte:<br>numerischer Real<br>(Standard: 3.0 - entspricht der HLS-Spezifikation) | Nur HLS |
| vebufferLength | Die Anzahl der Sekunden ab dem Live-Point, die in Verbindung mit vetargetmultiplier verwendet werden.<br>Hinweis: Dieser Parameter gilt nur für Live-/Linear-HLS-Streams<br>Mögliche Werte:<br>numerischer Real<br>(Standard: 3.0) | Nur HLS |
