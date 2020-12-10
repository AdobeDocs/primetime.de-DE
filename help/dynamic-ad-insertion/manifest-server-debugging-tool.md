---
title: Manifestserver-Debugging-Tool
seo-title: Manifestserver-Debugging-Tool
description: Manifestserver-Debugging-Tool
seo-description: Manifestserver-Debugging-Tool
uuid: 0b4f06f5-4b1f-4f88-980a-5b4df28e0094
products: SG_PRIMETIME
topic-tags: ad-insertion
discoiquuid: 00b49659-ce56-4b5c-87cd-c357a0936641
donotlocalize: false
moreHelpPaths: /content/help/en/primetime/morehelp/ad-insertion;/content/help/en/primetime/morehelp/ad-insertion
pagecreatedat: en
pagelayout: video
sidecolumn: left
translation-type: tm+mt
source-git-commit: 3efbd1113e82c4d5f84798997b6f744daf6f508e
workflow-type: tm+mt
source-wordcount: '2437'
ht-degree: 0%

---


# Manifest-Server-Debugging-Tool {#manifest-server-debugging-tool}

## Übersicht über das Debugging-Tool {#overview-of-debugging-tool}

Das Debugging-Tool ermöglicht es Herausgebern, potenziell kostspielige Probleme beim Einfügen von Anzeigen zu untersuchen, indem Debugging-Informationen geprüft werden, die vom Manifestserver in Echtzeit in HTTP-Headern zurückgegeben werden, oder, wenn detailliertere Informationen erforderlich sind, Sitzungsprotokolle nach dieser Tatsache geprüft werden. Adoben-Partner wie Akamai können das Tool zum Debugging ihrer Integrationen mit Primetime- und Entscheidungsfindung verwenden.

Das Tool unterstützt Debugging- und Einfügeprobleme in allen Hauptmanifestserver- und Verfolgungskonfigurationen:

* Clientseitige Verfolgung mit einem Player, der auf TVSDK basiert.
* Clientseitige Verfolgung mit einem Player, der nicht auf TVSDK basiert.
* Serverseitige Verfolgung.

Um alle diese Fälle zu unterstützen, benötigt das Tool keine Player-Herausgebercodes oder verwendet diese.

Wenn Sie eine Manifestserversitzung starten, können Sie einen Parameter in der Anforderungs-URL festlegen, um ihn zur Protokollierung der Debugging-Informationen aufzufordern. Mithilfe verschiedener Werte dieses Parameters können Sie den Manifestserver auch auffordern, bestimmte Teile von Debugging-Informationen in HTTP-Headern zurückzugeben. Header können jedoch nur eine begrenzte Anzahl von Informationen enthalten. Sie können Anmeldeinformationen von der Adobe abrufen, um auf vollständige Protokolldateien zuzugreifen, die vom Manifestserver regelmäßig (z. B. stündlich) auf einem Archivserver gespeichert werden. Sobald Sie über Anmeldeinformationen für diesen Server verfügen, können Sie jederzeit direkt darauf zugreifen.

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## Debugging-Tool-Optionen {#debugging-tool-options}

Beim Aufrufen des Debuggingwerkzeugs stehen Ihnen verschiedene Optionen zur Verfügung, um zu ermitteln, welche Informationen der Manifestserver in HTTP-Headern zurückgibt. Die Optionen wirken sich nicht darauf aus, was der Manifest-Server in Protokolldateien ablegt.

### Festlegen von ptdebug {#specifying-ptdebug}

Wenn Sie die Debug-Protokollierung für eine Manifest-Serversitzung initiieren, können Sie der Anforderungs-URL den Parameter ptdebug hinzufügen, um die folgenden Optionen für die Informationen anzugeben, die der Manifest-Server in HTTP-Headern zurückgibt:

* ptdebug=true Alle Datensätze außer `TRACE_HTTP_HEADER` und die meisten `call/response data` von `TRACE_AD_CALL`-Datensätzen.
* ptdebug=Nur AdCall-TRACE_AD_*type* (z. B. TRACE_AD_CALL)-Datensätze.
* ptdebug=Nur TRACE_HTTP_HEADER-Datensätze für Header.

Die Optionen wirken sich nicht darauf aus, was der Manifest-Server in den Protokolldateien ablegt. Sie haben keine Kontrolle darüber, aber die Protokolldateien sind Textdateien, sodass Sie eine Vielzahl von Tools anwenden können, um die Informationen zu extrahieren und neu zu formatieren, die Sie interessieren.

Hier ist ein Beispiel für den HTTP-Header, der zurückgegeben wird, wenn `ptdebug=Header`. Einige lange Zeichenfolgen mit hexadezimalen Ziffern werden aus Gründen der Klarheit durch `. . .` ersetzt.

```
X-ADBE-AI-DBG-1 TRACE_MISC    HTTP request received
X-ADBE-AI-DBG-2 TRACE_MISC    Processing Variant
X-ADBE-AI-DBG-3 TRACE_MISC    Valid URL received.
X-ADBE-AI-DBG-4 TRACE_MISC    Initialize new session
X-ADBE-AI-DBG-5 TRACE_MISC    Requesting: /auditude/variant/pubAsset/aHR0cDovL . . .m3u8
 ?u=cecebae . . .&z=189962&pttrackingmode=simple&pttrackingversion=v1
 &ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true
X-ADBE-AI-DBG-6  TRACE_HTTP_HEADER  MAIN  REQUEST  Host    bWFuaWZl. . .
X-ADBE-AI-DBG-7  TRACE_HTTP_HEADER  MAIN  REQUEST  Connection       Y2xvc2U=
X-ADBE-AI-DBG-8  TRACE_HTTP_HEADER  MAIN  REQUEST  Accept   dGV4dC. . .
X-ADBE-AI-DBG-9  TRACE_HTTP_HEADER  MAIN  REQUEST  Cookie   c3NhaT. . .
X-ADBE-AI-DBG-10 TRACE_HTTP_HEADER  MAIN  REQUEST  User-Agent       TW96aWxs. . .
X-ADBE-AI-DBG-11 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Language  ZW4tdXM=
X-ADBE-AI-DBG-12 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Encoding  Z3ppcCwg. . .=
X-ADBE-AI-DBG-13 TRACE_REQUEST_INFO  200   GET
 /auditude/variant/pubAsset/aHR0cD. . ..m3u8
 ?u=cecebae72a919de350b9ac52602623f3&z=189962&pttrackingmode=simple
 &pttrackingversion=v1&ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true   0 0 0   Variant  NA  null  null  127.0.0.1:43357
X-ADBE-AI-DBG-14 TRACE_HTTP_HEADER  MAIN  RESPONSE Content-Type     YXBwbG. . .
X-ADBE-AI-DBG-15 TRACE_HTTP_HEADER  MAIN  RESPONSE Cache-Control    bm8tY2. . .
X-ADBE-AI-DBG-16 TRACE_HTTP_HEADER  MAIN  RESPONSE Access-Control-Allow-Origin    Kg==
X-ADBE-AI-DBG-17 TRACE_MISC   Done
```

## Formate der Protokolldatensätze {#formats-of-log-records}

Jeder Protokolldatensatz verfügt über einen Typ und eine Reihe von Feldern, von denen einige optional sein können. Die Felder aller Datensätze bis zum Datensatztyp sind identisch. Sie stellen einen Zeitstempel und Informationen über die Sitzung bereit. Der Datensatztyp identifiziert die Art des Ereignisses, das protokolliert wird, und nachfolgende Felder enthalten Informationen über das protokollierte Ereignis.

Die Struktur eines Protokolldatensatzes lautet wie folgt:

`datetime request_id session_id zone_id record_type` *andere Felder.*

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| datetime | string | Zeitstempel |
| request_id | string | Vom Manifestserver verwendete Anforderungs-ID (Unix-Zeitstempel) |
| session_id | string | Vom Manifestserver verwendete Sitzungs-ID |
| zone_id | integer | Zone-ID |
| record_type | string | Art des protokollierten Ereignisses |
| andere Felder | *** | Abhängig vom Ereignistyp |

### TRACE_REQUEST_INFO records {#trace-request-info-records}

Datensätze dieses Typs protokollieren die Ergebnisse von HTTP-Anfragen. Felder, die über TRACE_REQUEST_INFO hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| request_method | string | HTTP-Methode (GET oder POST) |
| request_uri | string | HTTP-Anforderungs-URI (ohne Host) |
| request_length | integer | Länge der Anforderung (Byte) |
| response_length | integer | Länge der Antwort (Byte) |
| delta | integer | Zeit (Millisekunden) für die Verarbeitung der Anforderung |
| module_type | string | Variante, Stream oder VOD |
| remote_address_aud_client_ip | string | (siehe Hinweis) |
| remote_address_x_fwd_for_hdr_key | string | (siehe Hinweis) |
| remote_host_port | string | (siehe Hinweis) |

>[!NOTE]
>
>Die letzten drei Felder sind optional.

Beispiel:

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER records {#trace-http-header-records}

Datensätze dieses Typs protokollieren HTTP-Header, die während HTTP-Aufrufen zwischen dem Manifestserver und dem Client, dem Ad-Server oder dem Inhaltsserver ausgetauscht werden. Felder, die über TRACE_HTTP_HEADER hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Tabulatoren.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| request_type | string | Art des Antrags (MAIN oder UNBEKANNT) |
| request_response | string | Antwort-Header (Anfrage oder Antwort) |
| header_name | string | HTTP-Headername |
| header_value | string | Base64-kodierter HTTP-Header-Wert |

>[!NOTE]
>
>Die Felder request_type und header_value sind optional.

Beispiel:

```
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_MISC
    Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST Cookie  aGRu. . .
2015-03-25T06:10:00.928Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST User-Agent  TW96aW. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Server  bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Content-Type    YXBwb. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Last-Modified   V2VkL. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  ETag    IjIyY2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Vary    QWNjZXB. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Cache-Control   bWF4LW. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Expires V2VkL. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Date    V2VkLCA. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Age MQ==
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Via MS4xIH. . .
```

### TRACE_AD_CALL records {#trace-ad-call-records}

Datensätze dieses Typs protokollieren die Ergebnisse von Manifest-Server- und -Anforderungen. Felder, die über TRACE_AD_CALL hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Tabulatoren.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| request_duration | integer | Zeit (Millisekunden) von Anforderung bis Antwort |
| ad_server_Abfrage_url | string | URL für den Anzeigenaufruf, einschließlich Abfrageparameter |
| ad_system_id | string | Anzeigesystem von der Anzeigenserver-Antwort (Auditude, falls nicht angegeben) |
| avail_id | string | ID des avail, from the ad cue in the content manifest file (N/A for VOD) |
| avail_duration | number | Dauer (Sekunden) des Nutzens, ausgehend von der Anzeige in der Inhaltsmanifestdatei (N/A für VOD) |
| ad_server_response | string | Base64-codierte Antwort vom Ad-Server |

Beispiel:

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE und TRACE_AD_REDIRECT records {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

Datensätze dieses Typs protokollieren die Ergebnisse der Anzeigenanforderungen, die durch den Datensatztyp angegeben sind. Felder, die über den Datensatztyp hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabulatoren.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| avail_id | string | ID des avail, aus dem ad cue in der content manifest file (live) oder vom manifest server (VOD) |
| ad_type | string | Art der Anzeige (DIREKT oder UMLEITUNG) |
| ad_duration | integer | Dauer (Sekunden) der Anzeige von der Ad-Server-Antwort |
| ad_content_url | string | URL der Manifestdatei der Anzeige, von der Antwort des Anzeigenservers |
| ad_content_url_IST | string | URL der Manifestdatei der eingefügten Anzeige. Leer für TRACE_AD_REDIRECT. |
| ad_system_id | string | Anzeigesystem von der Anzeigenserver-Antwort (Auditude, falls nicht angegeben) |
| ad_id | string | ID der Anzeige von der Antwort des Anzeigenservers |
| creative_id | string | ID des Kreativen, vom Knoten ad, von der Antwort des Anzeigenservers |
| ad_call_id | string | Nicht verwendet. Reserviert für zukünftige Verwendung. |
| delta | integer | Von diesem Ereignis eingenommene Zeit (Millisekunden) |
| misc | string | Grund-Anzeige wurde übersprungen |

>[!NOTE]
>
>Die Felder ad_content_url_actual, ad_call_id und misc sind optional.

Für TRACE_AD_RESOLVE und TRACE_AD_INSERT gilt die URL im Feld ad_content_url_actual für die transcodierte Anzeige, sofern eine verfügbar ist. Andernfalls ist das Feld für TRACE_AD_RESOLVE leer oder für TRACE_AD_INSERT identisch mit ad_content_url.

Beispiel:

```
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

### TRACE_TRACKING_URL records {#trace-tracking-url-records}

Datensätze dieses Typs protokollieren die Ergebnisse von Manifest-Server- und -Anforderungen. Felder, die über TRACE_TRACKING_URL hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| pts | number | Programmzeitstempel. Zeit innerhalb des Videos, um die URL aufzurufen. |
| ad_system | string | Anzeigesystem (Auditude oder Freiräder) |
| url | string | URL pinged |
| Status | string | Vom Ping zurückgegebener HTTP-Status |

Beispiel:

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode-records}

Datensätze dieser Art protokollieren eine fehlende und kreative Anzeige. Das einzige Feld, das über TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE hinausgeht, wird in der Tabelle angezeigt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| ad_id | string | Vollqualifizierte Ad-ID `(FQ_AD_ID: Q_AD_ID[;Q_AD_ID[;Q_AD_ID...]]` Q_AD_ID: `PROTOCOL:AD_SYSTEM:AD_ID[:CREATIVE_ID[:MEDIA_ID]]` PROTOKOLL: AUDITUDE, VAST`)` |

### TRACE_TRANSCODING_REQUESTED records {#trace-transcoding-requested-records}

Datensätze dieses Typs protokollieren die Ergebnisse von Transkodierungsanforderungen, die der Manifestserver an das CRS sendet. Felder, die über TRACE_TRANSCODING_REQUESTED hinausgehen, werden in der in der Tabelle angegebenen Reihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| ad_id | string | Vollständig qualifizierte Ad-ID |
| ad_manifest_url | string | URL der Manifestdatei der Anzeige, von der Antwort des Anzeigenservers |
| creative_type | string | Medientyp |
| Markierungen | string | ID3 gibt an, ob die Transkodierungsanforderung eine Anforderung zum Hinzufügen eines ID3-Tags enthält |
| zielgruppe_duration | string | Zieldauer (Sekunden) der transcodierten Kreativelösung |

### TRACE_TRACKING_REQUEST records {#trace-tracking-request-records}

Datensätze dieses Typs weisen auf eine Anforderung zur serverseitigen Verfolgung hin. Felder, die über TRACE_TRACKING_REQUEST hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| tracking_url_count | integer | Anzahl der Tracking-URLs |
| beginn | float | Startzeit des PTS-Fragments (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | Endzeit des PTS-Fragments (Sekunden mit Millisekunde-Genauigkeit) |

### TRACE_TRACKING_REQUEST_URL records {#trace-tracking-request-url-records}

Datensätze dieses Typs enthalten eine Tracking-URL für die serverseitige Verfolgung. Felder, die über TRACE_TRACKING_REQUEST_URL hinausgehen, werden in der in der Tabelle angegebenen Reihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Zeitstempel | float | Dauer (Sekunden mit Präzision 0,001) innerhalb der Wiedergabesitzung zum Pingen der Tracking-URL |
| ad_system | string | Anzeigesystem (z. B. Auditude) |
| url | string | URL zu ping |

### TRACE_WEBVTT_REQUEST records {#trace-webvtt-request-records}

Datensätze dieses Typs werden vom Manifest-Server für WEBVTT-Untertitel angefordert. Felder, die über TRACE_WEBVTT_REQUEST hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| vtt_uri | string | URL für Anforderung |
| beginn | float | Startzeit teilen (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | Endzeit teilen (Sekunden mit Millisekunde-Genauigkeit) |

### TRACE_WEBVTT_RESPONSE records {#trace-webvtt-response-records}

Datensätze dieses Typs Log-Antworten, die der Manifest-Server an Clients sendet, um Anfragen für `WEBVTT`-Beschriftungen zu beantworten. Felder, die über `TRACE_WEBVTT_RESPONSE` hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabulatoren.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| Ansprechen | string | Base64-codierte Antwort an Client gesendet |

### TRACE_WEBVTT_SOURCE records {#trace-webvtt-source-records}

Datensätze dieser Art Log-Antworten auf Anfragen, die der Manifest-Server für WEBVTT-Untertitel erstellt. Felder, die über TRACE_WEBVTT_SOURCE hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Tabulatoren.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | Rückgegebener HTTP-Statuscode |
| Quelle | string | Base64-kodierter Original-VTT-Inhalt |


### TRACE_MISC records {#trace-misc-records}

Über diese Art von Datensätzen kann der Manifest-Server Ereignisse und Informationen protokollieren, die andernfalls nicht vorgesehen sind, wenn er Anzeigen aufnimmt. Das Feld hinter TRACE_MISC besteht aus einer Meldungszeichenfolge. Folgende Meldungen können angezeigt werden:

* Anzeige ignoriert :AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirectAd*, priorität=*priorität*
* Werbeplatzierung gab null zurück.
* und erfolgreich geheftet.
* Anruf fehlgeschlagen: *Fehlermeldung*.
* Hinzufügen von User-Agent zum Abrufen des Raw-Manifests: *user-agent*.
* Hinzufügen eines Cookies zum Abrufen des Raw-Manifests: [cookie]
* Falsche URL *angeforderte URL-Fehlermeldung*. (Varianten-URL konnte nicht analysiert werden)
* URL aufgerufen: URL *Rückgabe erhalten: Antwortcode*. ( Live-URL)
* URL aufgerufen: URL *Rückgabecode: Antwortcode*. ( VOD-URL)
* Konflikt beim Auflösen von Anzeigen: entweder eines der - mittleren oder mittleren Rollen-Endpunkte fällt in die Vorrollen- oder Vorrollen, die im mittleren Rollen (VOD) enthalten sind.
* Vom Handler für URI ausgelöste unbehandelte Ausnahme erkannt: *Anfrage-URL*.
* Generieren des Variantenmanifests abgeschlossen. (Variante)
* Generieren des Variantenmanifests abgeschlossen.
* Ausnahme bei der Verarbeitung von VAST-Umleitung *Umleitungs-URL *Fehler: *Fehlermeldung*.
* Die Playlist der Anzeige für *ad manifest URL* konnte nicht abgerufen werden.
* Zielmanifest konnte nicht generiert werden. (HLSManifestResolver)
* Fehler beim Analysieren der ersten Ad-Call-Antwort: *Fehlermeldung*.
* *GET|POST *Anforderung für Pfad konnte nicht verarbeitet werden: *Anfrage-URL*. (Live/VOD)
* Live-Manifest-Anforderung konnte nicht verarbeitet werden: *Anfrage-URL*. (Live)
* Variantenmanifest konnte nicht zurückgegeben werden: *Fehlermeldung*.
* Gruppen-ID konnte nicht validiert werden: *Gruppen-ID*.
* Raw-Manifest wird abgerufen: *Content URL*. (Live)
* Folgende VAST-Umleitung: *Umleitungs-URL*.
* Leere verfügbare Dateien gefunden. (VOD)
* *number *ads gefunden. (VOD)
* HTTP-Anforderung empfangen. (Sehr erste Meldung)
* Ignorieren der Anzeige, weil die Differenz zwischen der Anzeigenreaktionsdauer (*Ad-Response-Dauer *Sek.) und der tatsächlichen Anzeigendauer (*tatsächliche Dauer *Sek.) größer als das Limit ist. (HLSManifestResolver)
* Ignorierender Avail, der keinen ID-Wert angegeben hat. (GroupAdResolver.java)
* Ignorieren des Avatars, der einen ungültigen Zeitwert angegeben hat: *time *for availId = *avail ID*.
* Ignorieren des Avatars, der einen ungültigen Zeitwert angegeben hat: *duration *for availId = *avail ID*.
* Neue Sitzung initialisieren. (Variante)
* Ungültige HTTP-Methode. Es muss eine GET sein. (VOD)
* Ungültige HTTP-Methode. Nachverfolgungsanforderung muss eine GET sein. (Live)
* Ungültige URL *angeforderte URL-Fehlermeldung*. (Variante)
* Ungültige Gruppe. (HLSManifestResolver)
* Ungültige Anforderung. Beschriftung ist keine gültige Tracking-Anforderung. (VOD)
* Ungültige Anforderung. Untertitelanfragen müssen nach der Einrichtung der Sitzung erfolgen. (VOD)
* Ungültige Anforderung. Nachverfolgungsanforderung muss nach der Sitzungserstellung erfolgen. (VOD)
* Ungültige Serverinstanz für Überlastungs-Gruppen-ID: *Gruppen-ID*. (Live)
* Grenze der erreichten VAST-Umleitungen - *Zahl*.
* Anruf: *ad call URL*.
* Kein Manifest gefunden für: *Content URL*. (Live)
* Für die avail ID wurde kein passender Wert gefunden: *avail ID*. (HLSManifestResolver)
* Keine Wiedergabesitzung gefunden. (HLSManifestResolver)
* Verarbeitung der VOD-Anforderung für Manifest *Inhalt-URL*.
* Verarbeitungsvariante.
* Beschriftungsanforderung für Manifest *Inhalt-URL* wird verarbeitet.
* Verarbeiten der Tracking-Anforderung. (VOD)
* Umleitung und Antwort leer. (VASTStAX)
* Anforderung: *URL*.
* Die Fehlerantwort für die GET-Anforderung wird zurückgegeben, da keine Wiedergabesession gefunden wurde. (VOD)
* Die Fehlerantwort für die GET-Anforderung wird aufgrund eines internen Serverfehlers zurückgegeben.
* Fehlerantwort für eine GET-Anforderung zur Angabe eines ungültigen Elements wird zurückgegeben: *ad request ID*. (VOD)
* Fehlerantwort für eine GET-Anforderung, die eine ungültige oder leere Gruppen-ID angibt: *Gruppen-ID*. (VOD)
* Gibt die Fehlerantwort für eine GET-Anforderung zurück, die einen ungültigen Wert für die Tracking-Position angibt. (VOD)
* Fehlerantwort für eine GET-Anforderung mit ungültiger Syntax wird zurückgegeben - *Anfrage-URL*. (Live/VOD)
* Fehlerantwort für eine Anforderung mit nicht unterstützter HTTP-Methode wird zurückgegeben: *GET|POST*. (Live/VOD)
* Manifest wird aus dem Cache zurückgegeben. (VOD)
* Server ist überladen. Ohne Stich anfordern. (Variante)
* Beginnen Sie mit der Generierung des Zielmanifests. (HLSManifestResolver)
* Generieren des Variantenmanifests aus: *Content URL*. (Variante)
* Beginnen Sie mit dem Heften von Anzeigen in Manifest. (VODHLSResolver)
* Versucht, die Anzeige bei *HH:MM:SS* anzuheften: AdPlacement adManifestURL=*ad Manifest URL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirect ad*, priorität=*priorität&lt;a1/>.* (HLSManifestResolver)
* Wegen ungültiger pttimeline konnten keine Anzeigen abgerufen werden. Der Inhalt wurde ohne Anzeigen zurückgegeben. (VOD)
* Keine Anzeige möglich - zurückgegeben den Inhalt ohne Anzeigen. (VOD)
* Es kann keine Ad-Query abgerufen werden, und es wurde keine Inhalts-URL angegeben. (VOD)
* Gültige URL erhalten. (VOD/Variante)
* Variante M3U8 wurde nicht gefunden. (Variante)

### TRACE_TRACKING_URL records {#trace-tracking-url-records-1}

Der Manifestserver generiert solche Datensätze, nachdem er während des Workflows zur serverseitigen Verfolgung eine Tracking-URL aufruft. Felder, die über TRACE_TRACKING_URL hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| pts | number | PTS-Zeit im Stream |
| ad_system | string | Anzeigesystem (Hörgeräusch oder Freilaufrad) |
| url | string | URL pinged |
| state | string | HTTP-Statuscode |

### TRACE_PLAYBACK_PROGRESS records {#trace-playback-progress-records}

Der Manifest-Server generiert solche Datensätze, wenn er während des Workflows zur serverseitigen Verfolgung ein Signal über den Fortschritt bei der Wiedergabe erhält. Felder, die über TRACE_PLAYBACK_PROGRESS hinausgehen, werden in der Tabellenreihenfolge angezeigt, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| Status | string | HTTP-Statuscode |
| Bandbreite | integer | Bandbreite des Streams |
| pts | integer | PTS-Zeit im Stream |
| ms_time | integer | Zeitpunkt, zu dem vom Manifest-Server generierte Tracking-URL |
| url | string | Umleitungs-URL |
| header_user_agent | string | HTTP-User-Agent-Header |
| header_dnt | integer | HTTP-do-not-track-Header |
| effective_remote_address | string | IPv4-Remote-Adresse |
| remote_address | string | IPv4-Remote-Adresse |

>[!NOTE]
>
>Die letzten vier Felder sind optional.

## Hilfreiche Ressourcen {#helpful-resources}

* Weitere Informationen finden Sie in der vollständigen Hilfedokumentation auf der Seite [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
