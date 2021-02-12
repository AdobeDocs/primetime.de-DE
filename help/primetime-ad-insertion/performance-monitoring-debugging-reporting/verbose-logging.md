---
title: Ausführliche Protokollierung
description: null
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---


# Ausführliche Protokollierung {#verbose-logging}

## ptdebug/logging-Ereignis-Beschreibungen {#ptdebug-logging-events}

Beim Starten der Debug-Protokollierung für eine Manifestserversitzung können Sie den Parameter `ptdebug` zur Anforderungs-URL hinzufügen, um die folgenden Optionen für die Informationen anzugeben, die der Manifestserver in HTTP-Headern zurückgibt:

* `ptdebug=true`
Alle Datensätze außer TRACE_HTTP_HEADER und die meisten Call/Response-Daten aus TRACE_AD_CALL-Datensätzen.

* `ptdebug=AdCall`
Nur TRACE_AD_-Datensätze (z. B. TRACE_AD_CALL).

* `ptdebug=Header`
Nur TRACE_HTTP_HEADER-Datensätze.

## Formate der Protokolldatensätze {#log-record-formats}

Jeder Protokolldatensatz verfügt über einen Typ und eine Reihe von Feldern, von denen einige optional sein können. Die Felder aller Datensätze bis zum Datensatztyp sind gleich. Sie stellen einen Zeitstempel und Informationen zur Sitzung bereit. Der Datensatztyp identifiziert die Art des protokollierten Ereignisses, und nachfolgende Felder enthalten Informationen zum protokollierten Ereignis.

Die Struktur eines Protokolldatensatzes lautet wie folgt:

`datetime request_id session_id zone_id record_type other fields`.

| Feld | Typ | Beschreibung |
|---|---|---|
| datetime | string | Zeitstempel |
| request_id | string | Vom Manifestserver verwendete Antrags-ID (Unix-Zeitstempel) |
| session_id | string | Vom Manifestserver verwendete Sitzungs-ID |
| zone_id | integer | Zone |
| record_type | string | Typ des protokollierten Ereignisses |
| andere Felder | variiert | Abhängig vom Typ des Ereignisses |

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von HTTP-Anfragen. Felder, die über `TRACE_REQUEST_INFO` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | Rückgegebener HTTP-Statuscode |
| request_method | string | HTTP-Methode (GET oder POST) |
| request_uri | string | HTTP-Anforderungs-URI (ohne Host) |
| request_length | integer | Länge der Anforderung (Byte) |
| response_length | integer | Länge der Antwort (Byte) |
| delta | integer | Verarbeitungszeit (Millisekunden) |
| module_type | string | Variante, Stream oder VOD |
| remote_address_aud_client_ip | string | **□** |
| remote_address_x_fwd_for_hdr_key | string | **□** |
| remote_host_port | string | **□** |

****** Die letzten drei Felder sind optional.

**Beispiel**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER records {#trace-http-header-records}

Aufzeichnungen dieses Typs protokollieren HTTP-Header, die während HTTP-Aufrufen zwischen dem Manifestserver und dem Client, dem Anzeigenserver oder dem Inhaltsserver ausgetauscht wurden. Felder, die über &quot;TRACE_HTTP_HEADER&quot;hinausgehen, werden in der Tabellenreihenfolge durch Registerkarten getrennt angezeigt.

| Feld | Typ | Beschreibung |
|---|---|---|
| request_type | string | Art der Anforderung (MAIN oder UNKNOWN) |
| request_response | string | Antwortheader (Anforderung oder Antwort) |
| header_name | string | HTTP-Header-Name |
| header_value | string | Base64-kodierter HTTP-Header-Wert |

>[!NOTE]
>
>Die Felder `request_type` und `header_value` sind optional.

**Beispiel**

```shell
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_MISC Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST Cookie aGRu. . .
2015-03-25T06:10:00.928Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST User-Agent TW96aW. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Server bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Content-Type YXBwb. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Last-Modified V2VkL. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE ETag IjIyY2. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Vary QWNjZXB. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Cache-Control bWF4LW. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Expires V2VkL. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Date V2VkLCA. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Age MQ==
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Via MS4xIH. . .
```

### TRACE_AD_CALL records {#tracing-ad-call-records}

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von Manifestserver-Anzeigenanforderungen. Felder, die über `TRACE_AD_CALL` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | Rückgegebener HTTP-Statuscode |
| request_duration | integer | Zeit (Millisekunden) von Anforderung zu Antwort |
| ad_server_Abfrage_url | string | URL für den Anzeigenaufruf, einschließlich Abfrage-Parameter |
| ad_system_id | string | Anzeigensystem aus der Antwort des Anzeigenservers (Auditude, falls nicht angegeben) |
| avail_id | string | ID des Werts aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (K/A für VOD) |
| avail_duration | number | Dauer (Sekunden) des Werts, ausgehend vom Anzeigen-Cue in der Inhaltsmanifestdatei (K/A für VOD) |
| ad_server_response | string | Base64-kodierte Antwort vom Anzeigenserver |

Ein Beispiel:

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE und TRACE_AD_REDIRECT records {#trace-ad-insert-resolve-redirect}

Aufzeichnungen dieser Art protokollieren die Ergebnisse der Anzeigenanforderungen, die vom Datensatztyp angegeben werden. Felder, die über den Datensatztyp hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | HTTP-Statuscode zurückgegeben. |
| avail_id | string | ID des Avail, aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (live) oder vom Manifestserver (VOD). |
| ad_type | string | Art der Anzeige (DIRECT oder REDIRECT). |
| ad_duration | integer | Dauer (Sekunden) der Anzeige, von der Antwort des Anzeigenservers |
| ad_content_url | string | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers. |
| **☐** ad_content_url_IST | string | URL der Manifestdatei der eingefügten Anzeige. Leer für TRACE_AD_REDIRECT. |
| ad_system_id | string | Anzeigensystem aus der Antwort des Anzeigenservers (Auditude, falls nicht angegeben). |
| ad_id | string | ID der Anzeige aus der Antwort des Anzeigenservers. |
| creative_id | string | ID des kreativen Elements vom Anzeigenknoten aus der Antwort des Anzeigenservers. |
| **☐** ad_call_id | string | Nicht verwendet. Für zukünftige Verwendung reserviert. |
| delta | integer | Zeit (Millisekunden), die dieses Ereignis nimmt. |
| **☐** misc | string | Die Anzeige der Ursache wurde übersprungen. |

**☐** `ad_content_url_actual`,  `ad_call_id`und  `misc` Felder sind optional.

>[!NOTE]
>
>Bei `TRACE_AD_RESOLVE` und `TRACE_AD_INSERT` ist die URL im Feld `ad_content_url_actual` für die transkodierte Anzeige gültig, falls eine verfügbar ist. Andernfalls ist das Feld leer für `TRACE_AD_RESOLVE` oder dasselbe wie `ad_content_url` für `TRACE_AD_INSERT`.

Ein Beispiel:

```shell
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

<!-- ### TRACE_TRACKING_URL records {#trace-tracking-url-records}

Records of this type log the results of manifest server ad requests. Fields beyond `TRACE_TRACKING_URL` appear in the order shown in the table, separated by tabs.

| Field | Type | Description |
|---|---|---|
| pts | number | Program timestamp. Time within video to call the URL. |
| ad_system | string | Ad system (auditude or freewheel) |
| url | string | URL pinged |
| status | string | HTTP status returned from the ping |

```shell
2015-06-04T23:24:42.000-0700 1426742736208 3086f5cd . . . 12345 TRACE_TRACKING_URL 0.000000 ExampleSystem https://localhost/index.php?stream:test#8.1433485415; sid:3086f5cd . . .;pts:0 200
```

-->

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode}

Aufzeichnungen dieses Typs protokollieren ein fehlendes Werbekreativelement. Das einzige Feld nach `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` wird in der Tabelle angezeigt.

| Feld | Typ | Beschreibung |
|---|---|---|
| ad_id | string | Voll qualifizierte Anzeigen-ID (FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\] \] Q_AD_ID: PROTOKOLL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] PROTOKOLL: AUDITUDE,VAST) |

Aufzeichnungen dieses Typs protokollieren die Ergebnisse von Transkodierungsanforderungen, die der Manifestserver an das CRS sendet. Felder, die über `TRACE_TRANSCODING_REQUESTED` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| ad_id | string | Voll qualifizierte Anzeigen-ID |
| ad_manifest_url | string | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers |
| creative_type | string | Medientyp |
| Flags | string | ID3 gibt an, ob die Transkodierungsanforderung eine Anforderung zum Hinzufügen eines ID3-Tags enthält |
| zielgruppe_duration | string | Dauer der Zielgruppe (Sekunden) des transkodierten kreativen Elements |

Aufzeichnungen dieses Typs geben eine Anforderung zur serverseitigen Verfolgung an. Felder, die über `TRACE_TRACKING_REQUEST` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| tracking_url_count | integer | Anzahl der Tracking-URLs |
| beginn | float | PTS Fragment-Beginn (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | PTS-Fragmentendzeit (Sekunden mit Millisekunde-Genauigkeit) |

Datensätze dieses Typs bieten eine Tracking-URL für die serverseitige Verfolgung. Felder, die über `TRACE_TRACKING_REQUEST_URL` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| timestamp | float | Zeit (Sekunden mit Genauigkeit 0,001) innerhalb der Wiedergabesitzung, um die Tracking-URL zu pingen. |
| ad_system | string | Anzeigesystem (z. B. auditude) |
| url | string | URL zum Ping |

Datensätze dieses Typs protokollieren, die der Manifestserver für `WEBVTT`-Beschriftungen anfordert. Felder, die über `TRACE_WEBVTT_REQUEST` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | Rückgegebener HTTP-Statuscode |
| vtt_uri | string | URL für Anforderung |
| beginn | float | Beginn teilen (Sekunden mit Millisekunde-Genauigkeit) |
| end | float | Teilungsendzeit (Sekunden mit Millisekunde-Genauigkeit) |

Datensätze dieses Typs protokollieren Antworten, die der Manifestserver an Clients in `answer` an Anforderungen für `WEBVTT`-Beschriftungen sendet. Felder, die über `TRACE_WEBVTT_RESPONSE` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | Rückgegebener HTTP-Statuscode |
| response | string | Base64-kodierte Antwort an Client gesendet |

Datensätze dieses Typs protokollieren Antworten auf Anfragen, die der Manifestserver für `WEBVTT`-Beschriftungen ausführt. Felder, die über `TRACE_WEBVTT_SOURCE` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | Rückgegebener HTTP-Statuscode |
| source | string | Base64-kodierter Original-VTT-Inhalt |

Datensätze dieses Typs ermöglichen es dem Manifestserver, Ereignis und Informationen zu protokollieren, die andernfalls nicht vorgesehen sind, wenn Anzeigen aufgenommen werden. Das Feld nach `TRACE_MISC` besteht aus einer Meldungszeichenfolge. Folgende Meldungen können angezeigt werden:

* Anzeige ignoriert: AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= seconds, ignore= ignore, redirectAd= redirectAd, priority= priority
* Anzeigenplatzierung gab null zurück.
* Anzeige erfolgreich geheftet.
* Anzeigenaufruf fehlgeschlagen: Fehlermeldung.
* Hinzufügen von User-Agent zum Abrufen des unverarbeiteten Manifests: user-agent.
* Hinzufügen eines Cookies zum Abrufen des unverarbeiteten Manifests: #
* Fehlerhafte URL-angeforderte URL-Fehlermeldung. (Varianten-URL konnte nicht analysiert werden)
* URL aufgerufen: URL wurde zurückgegeben: Antwortcode. (Live-URL)
* URL aufgerufen: URL-Rückgabecode: Antwortcode. (VOD-URL)
* Konflikt beim Auflösen von Anzeigen: entweder eines der - Mid - Roll - oder Mid - Roll - Beginn innerhalb des Vorrollens oder Vorrollens in Mid - Roll (VOD).
* Vom Handler für URI ausgelöste nicht verarbeitete Ausnahme erkannt: Anforderungs-URL.
* Generiert das Variantenmanifest. (Variante)
* Generiert das Variantenmanifest.
* Ausnahme bei der Behandlung der VAST-Umleitung *Umleitungs-URL *Fehler: Fehlermeldung.
* Die Wiedergabeliste der Anzeige für die URL des Anzeigenmanifests konnte nicht abgerufen werden.
* Targeting-Manifest konnte nicht erstellt werden. (HLSManifestResolver)
* Die Antwort auf den ersten Anzeigenaufruf konnte nicht analysiert werden: Fehlermeldung.
* *GET|POST *Anfrage für Pfad konnte nicht verarbeitet werden: Anforderungs-URL. (Live/VOD)
* Live-Manifestanforderung konnte nicht verarbeitet werden: Anforderungs-URL. (Live)
* Fehler beim Zurückgeben eines Variantenmanifests: Fehlermeldung.
* Gruppen-ID konnte nicht validiert werden: Gruppen-ID.
* Rohes Manifest abrufen: Inhalts-URL. (Live)
* Nach VAST-Umleitung: Umleitungs-URL.
* Leer gefunden. (VOD)
* Anzeigen gefunden *number*. (VOD)
* HTTP-Anforderung empfangen. (Sehr erste Meldung)
* Die Anzeige wird ignoriert, weil die Differenz zwischen der Anzeigenantwortdauer (*Anzeigenreaktionsdauer *Sek.) und der tatsächlichen Anzeigendauer (*tatsächliche Dauer *Sek.) größer als die Beschränkung ist. (HLSManifestResolver)
* Ignoring avail that provided no ID value. (GroupAdResolver.java)
* Ignorieren von Werten, die einen ungültigen Zeitwert lieferten: *time *for availId = avail ID.
* Ignorieren von Werten, die einen ungültigen Wert für die Dauer boten: *duration *for availId = avail ID.
* Neue Sitzung initialisieren (Variante)
* Ungültige HTTP-Methode. Es muss eine GET sein. (VOD)
* Ungültige HTTP-Methode. Die Verfolgungsanfrage muss eine GET sein. (Live)
* Ungültige URL-angeforderte URL-Fehlermeldung. (Variante)
* Ungültige Gruppe. (HLSManifestResolver)
* Ungültige Anforderung. Beschriftung ist keine gültige Verfolgungsanforderung. (VOD)
* Ungültige Anforderung. Der Untertitelantrag muss nach der Einrichtung der Sitzung gestellt werden. (VOD)
* Ungültige Anforderung. Verfolgungsanfragen müssen nach der Einrichtung der Sitzung gestellt werden. (VOD)
* Ungültige Serverinstanz für Überlastungs-Gruppen-ID: Gruppen-ID. (Live)
* Grenze der VAST-Umleitungen erreicht - Zahl.
* Durchführen eines Anzeigenaufrufs: URL des Anzeigenaufrufs.
* Kein Manifest gefunden für: Inhalts-URL. (Live)
* Für die avail-ID wurde kein passender Wert gefunden: avail-ID. (HLSManifestResolver)
* Keine Wiedergabesitzung gefunden. (HLSManifestResolver)
* Verarbeitung der VOD-Anforderung für die URL des Manifestinhalts.
* Verarbeitungsvariante.
* Beschriftungsanforderung für die URL des Manifestinhalts wird verarbeitet.
* Verfolgungsanforderung wird verarbeitet. (VOD)
* Umleitungsanzeigeantwort leer. (VASTStAX)
* Anfordern: URL.
* Gibt die Fehlerantwort für die GET zurück, da keine Wiedergabesitzung gefunden wurde. (VOD)
* Gibt eine Fehlerantwort für eine GET aufgrund eines internen Serverfehlers zurück.
* Rückgabe der Fehlerantwort für eine GET-Anforderung zur Angabe eines ungültigen Assets: Anzeigen-Anfrage-ID. (VOD)
* Gibt eine Fehlerantwort für eine GET-Anforderung zurück, die eine ungültige oder leere Gruppen-ID angibt: Gruppen-ID. (VOD)
* Gibt eine Fehlerantwort für eine GET zurück, die einen Wert für eine ungültige Verfolgungsposition angibt. (VOD)
* Gibt die Fehlerantwort für eine GET mit ungültiger Syntax zurück - Anforderungs-URL. (Live/VOD)
* Gibt eine Fehlerantwort für eine Anforderung mit nicht unterstützter HTTP-Methode zurück: GET|POST. (Live/VOD)
* Gibt das Manifest aus dem Cache zurück. (VOD)
* Server wird überlastet. Fahren Sie ohne Anzeigenstitch-Anforderung fort. (Variante)
* Beginn, der ein zielgerichtetes Manifest generiert. (HLSManifestResolver)
* Beginn, der das Variantenmanifest generiert aus: Inhalts-URL. (Variante)
* Beginn, die Anzeigen in Manifest einbinden. (VODHLSResolver)
* Versuch, Anzeige bei `HH:MM:SS` zu verknüpfen: AdPlacement \[adManifestURL= Anzeigen-Manifest-URL, durationSeconds= seconds, ignore= ignore, redirectAd= redirect ad, priority= priority.\] \(HLSManifestResolver\)
* Wegen ungültiger pttimeline konnten keine Anzeigen abgerufen werden. Der Inhalt wurde ohne Anzeigen zurückgegeben. (VOD)
* Keine Anzeigen möglich - Inhalt ohne Anzeigen zurückgegeben. (VOD)
* Die Abfrage der Anzeige konnte nicht abgerufen werden, und es wurde keine Inhalts-URL angegeben. (VOD)
* Gültige URL empfangen. (VOD/Variante)
* Variante M3U8 nicht gefunden. (Variante)

### TRACE_PLAYBACK_PROGRESS records {#trace-playback-progress-records}

Der Manifestserver erzeugt solche Datensätze, wenn er während des Workflows zur serverseitigen Verfolgung ein Signal über den Fortschritt der Wiedergabe erhält. Felder, die über `TRACE_PLAYBACK_PROGRESS` hinausgehen, werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, durch Registerkarten getrennt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | string | HTTP-Statuscode |
| Bandbreite | integer | Bandbreite des Streams |
| pts | integer | PTS-Zeit im Stream |
| ms_time | integer | Zeitpunkt, zu dem der Manifestserver die Tracking-URL generiert hat |
| url | string | Umleitungs-URL |
| **¿** header_user_agent | string | HTTP User-Agent-Header |
| **¿** header_dnt | integer | HTTP do-not-track-Header |
| **¿** effective_remote_address | string | IPv4 effektive Remote-Adresse |
| **¿** remote_address | string | IPv4-Remote-Adresse |

**Die** letzten vier Felder sind optional.

## Mehrere Bitratenströme {#multiple-bitrate-streams}

Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.

Der Manifestserver verwendet die Informationen in der URL-Anforderung des Bootstrap des Clients, um die Wiedergabeliste für Inhaltsvarianten abzurufen. Es wird eine neue variante Wiedergabeliste mit Manifestserverlinks zu Stream-Inhalten generiert. Der Client verwendet diese zum Erstellen von Anzeigeneinfügeanforderungen. Die Inhaltsverknüpfungen auf Stream-Ebene des Manifestservers haben das folgende Format:

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/**
vodDer Manifestserver legt diesen Wert basierend auf dem Playlist-Typ des Inhalts fest: Interaktiv/linear (
`#EXT-X-PLAYLIST-TYPE:EVENT`) oder VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **Die eindeutige ID des**
publisherAssetIDPublisher für den spezifischen Bootstrap, der in der URL-Anforderung bereitgestellt wird.

* ****
renditionDer Manifestserver legt dies auf der Grundlage der Variablen 
`BANDWIDTH` Wert des Inhaltsstreams und verwendet ihn, um die Bitrate der Anzeige mit der Bitrate des Inhalts abzugleichen. Die Bitrate der Anzeige darf die Bitrate des Inhalts nur überschreiten, wenn die Anzeigenwiedergabe mit der niedrigsten Bitrate dies tut.

* ****
groupIDTder Manifestserver generiert diesen Wert und stellt damit sicher, dass er Anzeigen konsistent platziert, unabhängig davon, für welche Bitratendarstellungen der Client Anzeigen anfordert.

* **base64-kodierte URL des**
Streams mit BitrateDie URL-sichere Basis des Manifestservers64 kodiert die absolute URL des Inhaltsstreams. Jeder Stream hat seine eigene URL.

* **Abfrage**
parametersAbfrageparameter, die in der Bootstrap-URL-Anforderung bereitgestellt werden.
