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
source-git-commit: b77f4988103b68d0ce8926407d2ccb2e0c68e322

---


# Manifestserver-Debugging-Tool {#manifest-server-debugging-tool}

## Übersicht über das Debugging-Tool {#overview-of-debugging-tool}

Das Debugging-Tool ermöglicht es Herausgebern, potenziell kostspielige Probleme beim Einfügen von Anzeigen zu untersuchen, indem Debugging-Informationen geprüft werden, die vom Manifestserver in Echtzeit in HTTP-Headern zurückgegeben werden, oder, wenn detailliertere Informationen erforderlich sind, Sitzungsprotokolle nach dieser Tatsache geprüft werden. Adobe-Partner wie Akamai können das Tool zum Debugging ihrer Integrationen mit der Primetime-Anzeigenentscheidung verwenden.

Das Tool unterstützt Debugging- und Einfügeprobleme in allen Hauptmanifestserver- und Verfolgungskonfigurationen:

* Clientseitige Verfolgung mit einem Player, der auf TVSDK basiert.
* Clientseitige Verfolgung mit einem Player, der nicht auf TVSDK basiert.
* Serverseitige Verfolgung.

Um alle diese Fälle zu unterstützen, benötigt das Tool keine Player-Herausgebercodes oder verwendet diese.

Wenn Sie eine Manifestserversitzung starten, können Sie einen Parameter in der Anforderungs-URL festlegen, um ihn zur Protokollierung der Debugging-Informationen aufzufordern. Mithilfe verschiedener Werte dieses Parameters können Sie den Manifestserver auch auffordern, bestimmte Teile von Debugging-Informationen in HTTP-Headern zurückzugeben. Header können jedoch nur eine begrenzte Anzahl von Informationen enthalten. Sie können von Adobe Anmeldeinformationen abrufen, um auf vollständige Protokolldateien zuzugreifen, die vom Manifestserver regelmäßig (z. B. stündlich) auf einem Archivserver gespeichert werden. Sobald Sie über Anmeldeinformationen für diesen Server verfügen, können Sie jederzeit direkt darauf zugreifen.

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## Debugging-Tool-Optionen {#debugging-tool-options}

Beim Aufrufen des Debuggingwerkzeugs stehen Ihnen verschiedene Optionen zur Verfügung, um zu ermitteln, welche Informationen der Manifestserver in HTTP-Headern zurückgibt. Die Optionen wirken sich nicht darauf aus, was der Manifestserver in Protokolldateien ablegt.

### Festlegen von ptdebug {#specifying-ptdebug}

Beim Starten der Debug-Protokollierung für eine Manifestserversitzung können Sie den Parameter ptdebug zur Anforderungs-URL hinzufügen, um die folgenden Optionen für die Informationen festzulegen, die der Manifestserver in HTTP-Headern zurückgibt:

* ptdebug=true Alle Datensätze außer `TRACE_HTTP_HEADER` und die meisten `call/response data` aus `TRACE_AD_CALL` Datensätzen.
* ptdebug=Nur AdCall TRACE_AD_*type* (z. B. TRACE_AD_CALL) Datensätze.
* ptdebug=Nur Kopfzeile TRACE_HTTP_HEADER-Datensätze.

Die Optionen wirken sich nicht darauf aus, was der Manifestserver in den Protokolldateien ablegt. Sie haben keine Kontrolle darüber, aber die Protokolldateien sind Textdateien, sodass Sie eine Vielzahl von Tools anwenden können, um die Informationen, die Sie interessieren, zu extrahieren und neu zu formatieren.

Hier ein Beispiel für den HTTP-Header, der zurückgegeben wird, wenn `ptdebug=Header`. Einige lange Zeichenfolgen mit hexadezimalen Ziffern werden `. . .` aus Gründen der Klarheit ersetzt.

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

## Formate von Protokolldatensätzen {#formats-of-log-records}

Jeder Protokolldatensatz verfügt über einen Typ und eine Reihe von Feldern, von denen einige optional sein können. Die Felder aller Datensätze bis zum Datensatztyp sind gleich. Sie stellen einen Zeitstempel und Informationen zur Sitzung bereit. Der Datensatztyp identifiziert die Art des protokollierten Ereignisses, und nachfolgende Felder enthalten Informationen zum protokollierten Ereignis.

Die Struktur eines Protokolldatensatzes lautet wie folgt:

`datetime request_id session_id zone_id record_type` *andere Felder.*

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| datetime | string | Zeitstempel |
| request_id | string | Vom Manifestserver verwendete Antrags-ID (Unix-Zeitstempel) |
| session_id | string | Vom Manifestserver verwendete Sitzungs-ID |
| zone_id | integer | Zone-ID |
| record_type | string | Typ des protokollierten Ereignisses |
| andere Felder | *** | Abhängig vom Typ des Ereignisses |

### TRACE_REQUEST_INFO records {#trace-request-info-records}

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von HTTP-Anfragen. Felder, die über TRACE_REQUEST_INFO hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| request_method | string | HTTP-Methode (GET oder POST) |
| request_uri | string | HTTP-Anforderungs-URI (ohne Host) |
| request_length | integer | Länge der Anforderung (Byte) |
| response_length | integer | Länge der Antwort (Byte) |
| delta | integer | Verarbeitungszeit (Millisekunden) |
| module_type | string | Variante, Stream oder VOD |
| remote_address_aud_client_ip | string | (siehe Hinweis) |
| remote_address_x_fwd_for_hdr_key | string | (siehe Hinweis) |
| remote_host_port | string | (siehe Hinweis) |

>[!NOTE]
>
>Die letzten drei Felder sind optional.

Ein Beispiel:

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER records {#trace-http-header-records}

Aufzeichnungen dieses Typs protokollieren HTTP-Header, die während HTTP-Aufrufen zwischen dem Manifestserver und dem Client, dem Anzeigenserver oder dem Inhaltsserver ausgetauscht wurden. Felder, die über &quot;TRACE_HTTP_HEADER&quot;hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| request_type | string | Art der Anforderung (MAIN oder UNKNOWN) |
| request_response | string | Antwortheader (Anforderung oder Antwort) |
| header_name | string | HTTP-Header-Name |
| header_value | string | Base64-kodierter HTTP-Header-Wert |

>[!NOTE]
>
>Die Felder request_type und header_value sind optional.

Ein Beispiel:

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

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von Manifestserver-Anzeigenanforderungen. Felder, die über TRACE_AD_CALL hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| request_duration | integer | Zeit (Millisekunden) von Anforderung zu Antwort |
| ad_server_Abfrage_url | string | URL für den Anzeigenaufruf, einschließlich Abfrage-Parameter |
| ad_system_id | string | Anzeigensystem aus der Antwort des Anzeigenservers (Auditude, falls nicht angegeben) |
| avail_id | string | ID des Werts aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (K/A für VOD) |
| avail_duration | number | Dauer (Sekunden) des Werts, ausgehend vom Anzeigen-Cue in der Inhaltsmanifestdatei (K/A für VOD) |
| ad_server_response | string | Base64-kodierte Antwort vom Anzeigenserver |

Ein Beispiel:

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE und TRACE_AD_REDIRECT-Datensätze {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

Aufzeichnungen dieser Art protokollieren die Ergebnisse der Anzeigenanforderungen, die vom Datensatztyp angegeben werden. Felder, die über den Datensatztyp hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| avail_id | string | ID des Werts, aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (live) oder vom Manifestserver (VOD) |
| ad_type | string | Art der Anzeige (DIRECT oder REDIRECT) |
| ad_duration | integer | Dauer (Sekunden) der Anzeige, ab Ad-Server-Antwort |
| ad_content_url | string | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers |
| ad_content_url_IST | string | URL der Manifestdatei der eingefügten Anzeige. Leer für TRACE_AD_REDIRECT. |
| ad_system_id | string | Anzeigensystem aus der Antwort des Anzeigenservers (Auditude, falls nicht angegeben) |
| ad_id | string | ID der Anzeige aus der Antwort des Anzeigenservers |
| creative_id | string | ID des kreativen Elements vom Anzeigenknoten aus der Antwort des Anzeigenservers |
| ad_call_id | string | Nicht verwendet. Für zukünftige Verwendung reserviert. |
| delta | integer | Dauer (Millisekunden) dieses Ereignisses |
| misc | string | Die Anzeige aus Gründen wurde übersprungen |

>[!NOTE]
>
>Die Felder ad_content_url_IST, ad_call_id und misc sind optional.

Bei TRACE_AD_RESOLVE und TRACE_AD_INSERT ist die URL im Feld ad_content_url_IST für die transkodierte Anzeige, sofern eine verfügbar ist. Andernfalls ist das Feld leer für TRACE_AD_RESOLVE oder dasselbe wie ad_content_url für TRACE_AD_INSERT.

Ein Beispiel:

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

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von Manifestserver-Anzeigenanforderungen. Felder, die über TRACE_TRACKING_URL hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| pts | number | Programm-Zeitstempel. Zeit innerhalb des Videos, um die URL aufzurufen. |
| ad_system | string | Anzeigesystem (Auditude oder Freirad) |
| url | string | URL pinged |
| status | string | HTTP-Status, der vom Ping zurückgegeben wird |

Ein Beispiel:

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE-Datensätze {#trace-transcoding-no-media-to-transcode-records}

Aufzeichnungen dieses Typs protokollieren ein fehlendes Werbekreativelement. Das einzige Feld, das über TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE hinausgeht, wird in der Tabelle angezeigt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| ad_id | string | Voll qualifizierte Anzeigen-ID `(FQ_AD_ID: Q_AD_ID[;Q_AD_ID[;Q_AD_ID...]`] Q_AD_ID: `PROTOCOL:AD_SYSTEM:AD_ID[:CREATIVE_ID[:MEDIA_ID]`] PROTOKOLL: AUDITUDE,VAST) |

### TRACE_TRANSCODING_REQUESTED records {#trace-transcoding-requested-records}

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von Transkodierungsanforderungen, die der Manifestserver an das CRS sendet. Felder, die über TRACE_TRANSCODING_REQUESTED hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| ad_id | string | Voll qualifizierte Anzeigen-ID |
| ad_manifest_url | string | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers |
| creative_type | string | Medientyp |
| Flags | string | ID3 gibt an, ob die Transkodierungsanforderung eine Anforderung zum Hinzufügen eines ID3-Tags enthält |
| Zielgruppe_duration | string | Dauer der Zielgruppe (Sekunden) des transkodierten kreativen Elements |

### TRACE_TRACKING_REQUEST-Datensätze {#trace-tracking-request-records}

Aufzeichnungen dieses Typs geben eine Anforderung zur serverseitigen Verfolgung an. Felder, die über TRACE_TRACKING_REQUEST hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| tracking_url_count | integer | Anzahl der Tracking-URLs |
| Beginn | float | PTS Fragment-Beginn (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | PTS-Fragmentendzeit (Sekunden mit Millisekunde-Genauigkeit) |

### TRACE_TRACKING_REQUEST_URL records {#trace-tracking-request-url-records}

Datensätze dieses Typs bieten eine Tracking-URL für die serverseitige Verfolgung. Felder, die über TRACE_TRACKING_REQUEST_URL hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| timestamp | float | Zeit (Sekunden mit Genauigkeit 0,001) innerhalb der Wiedergabesitzung zum Pingen der Tracking-URL |
| ad_system | string | Anzeigesystem (z. B. auditude) |
| url | string | URL zum Ping |

### TRACE_WEBVTT_REQUEST-Datensätze {#trace-webvtt-request-records}

Datensätze dieses Typs protokollieren Anforderungen, die der Manifestserver für WEBVTT-Beschriftungen ausführt. Felder, die über TRACE_WEBVTT_REQUEST hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| vtt_uri | string | URL für Anforderung |
| Beginn | float | Beginn teilen (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | Teilungsendzeit (Sekunden mit Millisekunde-Genauigkeit) |

### TRACE_WEBVTT_RESPONSE records {#trace-webvtt-response-records}

Zeichnet ``of ``dieses ``type ``Protokoll ``responses ``des ``manifest ``Servers ``sends ``auf, ``clients ``bei `` `answer` ``den ``requests ```for` ``WEBVTT ``Untertiteln anzumelden. Felder, die über TRACE_WEBVTT_RESPONSE hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge angezeigt, durch getrennte `by`Registerkarten.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| response | string | Base64-kodierte Antwort an Client gesendet |

### TRACE_WEBVTT_SOURCE-Datensätze {#trace-webvtt-source-records}

Datensätze dieses Typs protokollieren Antworten auf Anfragen, die der Manifestserver für WEBVTT-Beschriftungen ausführt. Felder, die über TRACE_WEBVTT_SOURCE hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | Rückgegebener HTTP-Statuscode |
| source | string | Base64-kodierter Original-VTT-Inhalt |


### TRACE_MISC records {#trace-misc-records}

Datensätze dieses Typs ermöglichen es dem Manifestserver, Ereignis und Informationen zu protokollieren, die andernfalls nicht vorgesehen sind, wenn Anzeigen aufgenommen werden. Das Feld nach TRACE_MISC besteht aus einer Meldungszeichenfolge. Folgende Meldungen können angezeigt werden:

* Anzeige ignoriert :AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirectAd*, priority=*priority*
* Anzeigenplatzierung gab null zurück.
* Anzeige erfolgreich geheftet.
* Anzeigenaufruf fehlgeschlagen: *Fehlermeldung*.
* Hinzufügen von User-Agent zum Abrufen des unverarbeiteten Manifests: *user-agent*.
* Hinzufügen eines Cookies zum Abrufen des unverarbeiteten Manifests: [Cookie]
* Fehlerhafte URL- *angeforderte URL-Fehlermeldung*. (Varianten-URL konnte nicht analysiert werden)
* URL aufgerufen: URL *zurückgegeben: Antwortcode*. (Live-URL)
* URL aufgerufen: URL- *Rückgabecode: Antwortcode*. (VOD-URL)
* Konflikt beim Auflösen von Anzeigen: entweder eines der - Mid - Roll - oder Mid - Roll - Beginn innerhalb des Vorrollens oder Vorrollens in Mid - Roll (VOD).
* Vom Handler für URI ausgelöste nicht verarbeitete Ausnahme erkannt: URL der *Anforderung*.
* Generiert das Variantenmanifest. (Variante)
* Generiert das Variantenmanifest.
* Ausnahme bei der Behandlung der VAST-Umleitung *Umleitungs-URL *Fehler: *Fehlermeldung*.
* Die Wiedergabeliste der Anzeige für die *Anzeigen-Manifest-URL konnte nicht abgerufen werden*.
* Targeting-Manifest konnte nicht erstellt werden. (HLSManifestResolver)
* Die Antwort auf den ersten Anzeigenaufruf konnte nicht analysiert werden: *Fehlermeldung*.
* *GET|POST *Anfrage für Pfad konnte nicht verarbeitet werden: URL der *Anforderung*. (Live/VOD)
* Live-Manifestanforderung konnte nicht verarbeitet werden: URL der *Anforderung*. (Live)
* Fehler beim Zurückgeben eines Variantenmanifests: *Fehlermeldung*.
* Gruppen-ID konnte nicht validiert werden: *Gruppen-ID*.
* Rohes Manifest abrufen: URL des *Inhalts*. (Live)
* Nach VAST-Umleitung: URL *umleiten*.
* Leer gefunden. (VOD)
* *number *Anzeigen gefunden. (VOD)
* HTTP-Anforderung empfangen. (Sehr erste Meldung)
* Die Anzeige wird ignoriert, weil die Differenz zwischen der Anzeigenantwortdauer (*Anzeigenreaktionsdauer *Sek.) und der tatsächlichen Anzeigendauer (*tatsächliche Dauer *Sek.) größer als die Beschränkung ist. (HLSManifestResolver)
* Ignoring avail that provided no ID value. (GroupAdResolver.java)
* Ignorieren von Werten, die einen ungültigen Zeitwert lieferten: *time *for availId = *avail ID*.
* Ignorieren von Werten, die einen ungültigen Wert für die Dauer boten: *duration *for availId = *avail ID*.
* Neue Sitzung initialisieren (Variante)
* Ungültige HTTP-Methode. Es muss ein GET sein. (VOD)
* Ungültige HTTP-Methode. Die Verfolgungsanfrage muss ein GET sein. (Live)
* Ungültige URL- *angeforderte URL-Fehlermeldung*. (Variante)
* Ungültige Gruppe. (HLSManifestResolver)
* Ungültige Anforderung. Beschriftung ist keine gültige Verfolgungsanforderung. (VOD)
* Ungültige Anforderung. Der Untertitelantrag muss nach der Einrichtung der Sitzung gestellt werden. (VOD)
* Ungültige Anforderung. Verfolgungsanfragen müssen nach der Einrichtung der Sitzung gestellt werden. (VOD)
* Ungültige Serverinstanz für Überlastungs-Gruppen-ID: *Gruppen-ID*. (Live)
* Grenze der VAST-Umleitungen erreicht - *Zahl*.
* Durchführen eines Anzeigenaufrufs: URL *des Anzeigenaufrufs*.
* Kein Manifest gefunden für: URL des *Inhalts*. (Live)
* Für die avail-ID wurde kein passender Wert gefunden: *avail-ID*. (HLSManifestResolver)
* Keine Wiedergabesitzung gefunden. (HLSManifestResolver)
* Verarbeitung der VOD-Anforderung für die *URL* des Manifestinhalts.
* Verarbeitungsvariante.
* Beschriftungsanforderung für die *URL* des Manifestinhalts wird verarbeitet.
* Verfolgungsanforderung wird verarbeitet. (VOD)
* Umleitungsanzeigeantwort leer. (VASTStAX)
* Anfordern: *URL*.
* Gibt die Fehlerantwort für GET-Anforderung zurück, da keine Wiedergabesitzung gefunden wurde. (VOD)
* Ausgabe der Fehlerantwort für GET-Anforderung aufgrund eines internen Serverfehlers.
* Rückgabe der Fehlerantwort für eine GET-Anforderung zur Angabe eines ungültigen Assets: ID der *Anzeigenanforderung*. (VOD)
* Gibt eine Fehlerantwort für eine GET-Anforderung zurück, die eine ungültige oder leere Gruppen-ID angibt: *Gruppen-ID*. (VOD)
* Gibt eine Fehlerantwort für GET-Anforderung zurück, die einen ungültigen Wert für die Verfolgungsposition angibt. (VOD)
* Ausgabe der Fehlerantwort für GET-Anforderung mit ungültiger Syntax - *Anforderungs-URL*. (Live/VOD)
* Gibt eine Fehlerantwort für eine Anforderung mit nicht unterstützter HTTP-Methode zurück: *GET|POST*. (Live/VOD)
* Gibt das Manifest aus dem Cache zurück. (VOD)
* Server wird überlastet. Fahren Sie ohne Anzeigenstitch-Anforderung fort. (Variante)
* Beginn, der ein zielgerichtetes Manifest generiert. (HLSManifestResolver)
* Beginn, der das Variantenmanifest generiert aus: URL des *Inhalts*. (Variante)
* Beginn, die Anzeigen in Manifest einbinden. (VODHLSResolver)
* Verbinden der Anzeige mit *HH:MM:SS*: AdPlacement [adManifestURL=*Anzeigen-Manifest-URL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirect ad*, priority=*priority*. (HLSManifestResolver)
* Wegen ungültiger pttimeline konnten keine Anzeigen abgerufen werden. Der Inhalt wurde ohne Anzeigen zurückgegeben. (VOD)
* Keine Anzeigen möglich - Inhalt ohne Anzeigen zurückgegeben. (VOD)
* Die Abfrage der Anzeige konnte nicht abgerufen werden, und es wurde keine Inhalts-URL angegeben. (VOD)
* Gültige URL empfangen. (VOD/Variante)
* Variante M3U8 nicht gefunden. (Variante)

### TRACE_TRACKING_URL records {#trace-tracking-url-records-1}

Der Manifestserver generiert solche Datensätze, nachdem während des Workflows zur serverseitigen Verfolgung eine Tracking-URL aufgerufen wurde. Felder, die über TRACE_TRACKING_URL hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| pts | number | PTS-Zeit im Stream |
| ad_system | string | Anzeigensystem (Auditude oder Freiraum) |
| url | string | URL pinged |
| state | string | HTTP-Statuscode |

### TRACE_PLAYBACK_PROGRESS records {#trace-playback-progress-records}

Der Manifestserver erzeugt solche Datensätze, wenn er während des Workflows zur serverseitigen Verfolgung ein Signal über den Fortschritt der Wiedergabe erhält. Felder, die über TRACE_PLAYBACK_PROGRESS hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|--- |--- |--- |
| status | string | HTTP-Statuscode |
| Bandbreite | integer | Bandbreite des Streams |
| pts | integer | PTS-Zeit im Stream |
| ms_time | integer | Zeitpunkt, zu dem der Manifestserver die Tracking-URL generiert hat |
| url | string | Umleitungs-URL |
| header_user_agent | string | HTTP User-Agent-Header |
| header_dnt | integer | HTTP do-not-track-Header |
| effective_remote_address | string | IPv4 effektive Remote-Adresse |
| remote_address | string | IPv4-Remote-Adresse |

>[!NOTE]
>
>Die letzten vier Felder sind optional.

## Hilfreiche Ressourcen {#helpful-resources}

* Siehe vollständige Hilfedokumentation auf der Seite &quot; [Adobe Primetime - Training und Support](https://helpx.adobe.com/support/primetime.html) &quot;.
