---
title: Verbose protokollieren
description: Verbose protokollieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---

# Verbose protokollieren {#verbose-logging}

## Beschreibung des ptdebug/logging-Ereignisses {#ptdebug-logging-events}

Beim Starten der Debug-Protokollierung für eine Manifestserver-Sitzung können Sie die `ptdebug` Parameter zur Anfrage-URL hinzufügen, um die folgenden Optionen für die Informationen anzugeben, die der Manifestserver in HTTP-Headern zurückgibt:

* `ptdebug=true`
Alle Datensätze außer TRACE_HTTP_HEADER und den meisten Aufruf-/Antwortdaten aus TRACE_AD_CALL-Datensätzen.

* `ptdebug=AdCall`
Nur Datensätze vom Typ TRACE_AD_ (z. B. TRACE_AD_CALL).

* `ptdebug=Header`
Nur TRACE_HTTP_HEADER-Datensätze.

## Formate von Protokolldatensätzen {#log-record-formats}

Jeder Protokolldatensatz hat einen Typ und eine Reihe von Feldern, von denen einige optional sein können. Die Felder aller Datensätze bis zum Datensatztyp sind identisch. Sie stellen einen Zeitstempel und Informationen zur Sitzung bereit. Der Datensatztyp identifiziert die Art des zu protokollierenden Ereignisses und nachfolgende Felder enthalten Informationen zum protokollierten Ereignis.

Die Struktur eines Protokolldatensatzes sieht wie folgt aus:

`datetime request_id session_id zone_id record_type other fields`.

| Feld | Typ | Beschreibung |
|---|---|---|
| datetime | Zeichenfolge | Zeitstempel |
| request_id | Zeichenfolge | Vom Manifestserver verwendete Anforderungs-ID (Unix-Zeitstempel) |
| session_id | Zeichenfolge | Vom Manifestserver verwendete Sitzungs-ID |
| zone_id | integer | Bereich |
| record_type | Zeichenfolge | Typ des protokollierten Ereignisses |
| andere Felder | variieren | Abhängig vom Ereignistyp |

Datensätze dieses Typs protokollieren die Ergebnisse von HTTP-Anfragen. Felder jenseits `TRACE_REQUEST_INFO` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code |
| request_method | Zeichenfolge | HTTP-Methode (GET oder POST) |
| request_uri | Zeichenfolge | HTTP-Anfrage-URI (ohne Host) |
| request_length | integer | Anforderungslänge (Byte) |
| response_length | integer | Länge der Antwort (Byte) |
| delta | integer | Zeit (Millisekunden) für die Verarbeitung der Anforderung |
| module_type | Zeichenfolge | Variante, Stream oder VOD |
| remote_address_aud_client_ip | Zeichenfolge | **‡** |
| remote_address_x_fwd_for_hdr_key | Zeichenfolge | **‡** |
| remote_host_port | Zeichenfolge | **‡** |

**‡** Die letzten drei Felder sind optional.

**Beispiel**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER-Datensätze {#trace-http-header-records}

Datensätze dieses Typs protokollieren HTTP-Header, die während HTTP-Aufrufen zwischen dem Manifestserver und Client, Adserver oder Inhaltsserver ausgetauscht werden. Die Felder über TRACE_HTTP_HEADER hinaus werden in der Reihenfolge angezeigt, die in der Tabelle angezeigt wird, getrennt durch Registerkarten.

| Feld | Typ | Beschreibung |
|---|---|---|
| request_type | Zeichenfolge | Art der Anforderung (MAIN oder UNKNOWN) |
| request_response | Zeichenfolge | Antwortheader (Anfrage oder Antwort) |
| header_name | Zeichenfolge | HTTP-Headername |
| header_value | Zeichenfolge | Base64-kodierter HTTP-Header-Wert |

>[!NOTE]
>
>Die `request_type` und `header_value` -Felder sind optional.

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

### TRACE_AD_CALL-Datensätze {#tracing-ad-call-records}

Datensätze dieses Typs protokollieren die Ergebnisse von Manifestserver-Anzeigenanfragen. Felder jenseits `TRACE_AD_CALL` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code |
| request_duration | integer | Zeit (Millisekunden) von Anforderung zu Antwort |
| ad_server_query_url | Zeichenfolge | URL für den Anzeigenaufruf, einschließlich Abfrageparameter |
| ad_system_id | Zeichenfolge | Anzeigensystem aus der Anzeigenserverantwort (Auditude, falls nicht angegeben) |
| avail_id | Zeichenfolge | Kennung des Werts aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (nicht zutreffend für VOD) |
| avail_duration | number | Dauer (Sekunden) des Wertes vom Anzeigen-Cue in der Inhaltsmanifestdatei (nicht zutreffend für VOD) |
| ad_server_response | Zeichenfolge | Base64-kodierte Antwort vom Anzeigen-Server |

Beispiel:

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT-, TRACE_AD_RESOLVE- und TRACE_AD_REDIRECT-Datensätze {#trace-ad-insert-resolve-redirect}

Datensätze dieses Typs protokollieren die Ergebnisse der Anzeigenanfragen, die durch den Datensatztyp angegeben sind. Felder, die über den Datensatztyp hinausgehen, werden in der in der Tabelle angezeigten Reihenfolge durch Tabs getrennt angezeigt.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code. |
| avail_id | Zeichenfolge | Kennung des Wertes, aus dem Anzeigen-Cue in der Inhaltsmanifestdatei (live) oder vom Manifestserver (VOD). |
| ad_type | Zeichenfolge | Art der Anzeige (DIRECT oder REDIRECT). |
| ad_duration | integer | Dauer (Sekunden) der Anzeige, von der Antwort des Anzeigen-Servers |
| ad_content_url | Zeichenfolge | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers. |
| **†** ad_content_url_IST | Zeichenfolge | URL der Manifestdatei der eingefügten Anzeige. Leer für TRACE_AD_REDIRECT. |
| ad_system_id | Zeichenfolge | Anzeigensystem aus der Anzeigenserver-Antwort (Auditude, falls nicht angegeben). |
| ad_id | Zeichenfolge | ID der Anzeige aus der Antwort des Anzeigenservers. |
| creative_id | Zeichenfolge | ID des Kreativbereichs vom Anzeigenknoten aus der Antwort des Anzeigenservers. |
| **†** ad_call_id | Zeichenfolge | Nicht verwendet. Für zukünftige Verwendung reserviert. |
| delta | integer | Zeit (Millisekunden), die von diesem Ereignis benötigt wird. |
| **†** misc | Zeichenfolge | Die Reason-Anzeige wurde übersprungen. |

**†** `ad_content_url_actual`, `ad_call_id`, und `misc` -Felder sind optional.

>[!NOTE]
>
>Für `TRACE_AD_RESOLVE` und `TRACE_AD_INSERT`, die URL in der `ad_content_url_actual` -Feld für die transkodierte Anzeige verwendet wird, sofern verfügbar. Andernfalls ist das Feld leer für `TRACE_AD_RESOLVE` oder denselben `ad_content_url` für `TRACE_AD_INSERT`.

Beispiel:

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

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE-Datensätze {#trace-transcoding-no-media-to-transcode}

Datensätze dieses Typs protokollieren einen fehlenden Anzeigenkreativ. Das einzige Feld jenseits `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` in der Tabelle angezeigt.

| Feld | Typ | Beschreibung |
|---|---|---|
| ad_id | Zeichenfolge | Vollständig qualifizierte Anzeigen-ID (FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID..\] \] Q_AD_ID: PROTOCOL.:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] PROTOCOL: AUDITUDE,VAST |

Datensätze dieses Typs protokollieren die Ergebnisse von Transkodierungsanfragen, die der Manifestserver an CRS sendet. Felder jenseits `TRACE_TRANSCODING_REQUESTED` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| ad_id | Zeichenfolge | Vollständig qualifizierte Anzeigen-ID |
| ad_manifest_url | Zeichenfolge | URL der Manifestdatei der Anzeige aus der Antwort des Anzeigenservers |
| creative_type | Zeichenfolge | Medientyp |
| Flags | Zeichenfolge | ID3 gibt an, ob die Transkodierungsanforderung eine Anforderung zum Hinzufügen eines ID3-Tags enthält |
| target_duration | Zeichenfolge | Zieldauer (Sekunden) der transkodierten kreativen Inhalte |

Datensätze dieses Typs geben eine Anforderung zum serverseitigen Tracking an. Felder jenseits `TRACE_TRACKING_REQUEST` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| tracking_url_count | integer | Anzahl der Tracking-URLs |
| start | float | Startzeit des PTS-Fragments (Sekunden mit Millisekundengenauigkeit) |
| end | float | Endzeit des PTS-Fragments (Sekunden mit Millisekundengenauigkeit) |

Datensätze dieses Typs bieten eine Tracking-URL für das serverseitige Tracking. Felder jenseits `TRACE_TRACKING_REQUEST_URL` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| timestamp | float | Zeit (Sekunden, mit Genauigkeit von 0,001) innerhalb der Wiedergabesitzung, um die Tracking-URL zu pingen. |
| ad_system | Zeichenfolge | Anzeigensystem (z. B. auditude) |
| url | Zeichenfolge | URL zu Ping |

Datensätze dieses Typs protokollieren, die der Manifestserver anfordert `WEBVTT` Beschriftungen. Felder jenseits `TRACE_WEBVTT_REQUEST` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code |
| vtt_uri | Zeichenfolge | URL für Anforderung |
| start | float | Aufspaltung Startzeit (Sekunden mit Millisekundengenauigkeit) |
| end | float | Aufspaltung der Endzeit (Sekunden mit Millisekundengenauigkeit) |

Datensätze dieses Typs protokollieren Antworten, die der Manifestserver an Clients in sendet `answer` für Anfragen an `WEBVTT` Beschriftungen. Felder jenseits `TRACE_WEBVTT_RESPONSE` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code |
| response | Zeichenfolge | Base64-kodierte Antwort an Client gesendet |

Datensätze dieses Typs von Protokollantworten zu Anforderungen, die der Manifestserver sendet `WEBVTT` Beschriftungen. Felder jenseits `TRACE_WEBVTT_SOURCE` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | Zurückgegebener HTTP-Status-Code |
| source | Zeichenfolge | Base64-kodierter ursprünglicher VTT-Inhalt |

Datensätze dieses Typs ermöglichen es dem Manifestserver, Ereignisse und Informationen zu protokollieren, die nicht anderweitig für die Aufnahme von Anzeigen geplant sind. Das Feld weiter `TRACE_MISC` besteht aus einer Meldungszeichenfolge. Folgende Nachrichten können angezeigt werden:

* Anzeige ignoriert: AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= seconds, ignore= ignore, redirectAd= redirectAd, priority= priority
* Anzeigenplatzierung gab null zurück.
* Anzeige erfolgreich zugeordnet.
* Anzeigenaufruf fehlgeschlagen: Fehlermeldung.
* Hinzufügen von User-Agent zum Abrufen des Rohmanifests: user-agent.
* Hinzufügen eines Cookies zum Abrufen des Rohmanifests: #
* Fehlerhafte URL-angeforderte URL-Fehlermeldung. (Variante-URL konnte nicht analysiert werden)
* URL aufgerufen: URL erhalten return: Antwort-Code. ( Live-URL)
* URL aufgerufen: URL return code: response code. ( VOD-URL)
* Konflikt beim Auflösen von Anzeigen: Entweder der Mid-Roll-Start oder das Mid-Roll-Ende fällt in den Pre-Roll- oder Pre-Roll-Bereich, der im Mid-Roll (VOD) enthalten ist.
* Vom Handler für URI: Anfrage-URL ausgelöste nicht verarbeitete Ausnahme erkannt.
* Erstellung des Variantenmanifests abgeschlossen. (Variante)
* Erstellung des Variantenmanifests abgeschlossen.
* Ausnahme bei der Verarbeitung von VAST-Umleitung *Umleitungs-URL *Fehler: Fehlermeldung.
* Die Wiedergabeliste der Anzeige konnte nicht für die URL des Anzeigenmanifests abgerufen werden.
* Zielgruppenmanifest konnte nicht generiert werden. (HLSManifestResolver)
* Erste Anzeigenaufrufantwort konnte nicht analysiert werden: Fehlermeldung.
* *GET|POST *Anfrage für Pfad konnte nicht verarbeitet werden: Anfrage-URL. (Live/VOD)
* Live-Manifest-Anfrage konnte nicht verarbeitet werden: Anfrage-URL. (Live)
* Variantenmanifest konnte nicht zurückgegeben werden: Fehlermeldung.
* Gruppe-ID konnte nicht validiert werden: Gruppen-ID.
* Abrufen des Rohmanifests: Inhalts-URL. (Live)
* Nach VAST-Umleitung: Umleitungs-URL.
* Leere Verfügbare gefunden. (VOD)
* Found *number* Anzeigen. (VOD)
* HTTP-Anfrage empfangen. (Sehr erste Nachricht)
* Ignorieren von Anzeigen, da die Differenz zwischen der Anzeigenreaktionsdauer (*Anzeigenantwort-Dauer *Sek.) und der tatsächlichen Anzeigendauer (*tatsächliche Dauer *Sek.) größer als der Grenzwert ist. (HLSManifestResolver)
* Nichtberücksichtigung des Werts, der keinen ID-Wert enthielt. (GroupAdResolver.java)
* Ignorieren von Werten, die einen ungültigen Zeitwert boten: *time *for availId = avail ID.
* Ignorieren von Werten, die einen ungültigen Dauerwert boten: *duration *für availId = avail ID.
* Initialisieren einer neuen Sitzung. (Variante)
* Ungültige HTTP-Methode. Es muss ein GET sein. (VOD)
* Ungültige HTTP-Methode. Die Tracking-Anfrage muss eine GET sein. (Live)
* Ungültige URL-angeforderte URL-Fehlermeldung. (Variante)
* Ungültige Gruppe. (HLSManifestResolver)
* Ungültige Anfrage. Beschriftung ist keine gültige Verfolgungsanforderung. (VOD)
* Ungültige Anfrage. Die Untertitelanforderung muss nach der Einrichtung der Sitzung erfolgen. (VOD)
* Ungültige Anfrage. Tracking-Anfragen müssen nach der Einrichtung der Sitzung gestellt werden. (VOD)
* Ungültige Serverinstanz für Überlastungs-Gruppen-ID: Gruppen-ID. (Live)
* Limit der erreichten VAST-Umleitungen - Zahl.
* Anruf der Anzeige: URL des Anzeigenaufrufs.
* Für wurde kein Manifest gefunden: Inhalts-URL. (Live)
* Für die avail ID wurde kein übereinstimmender Wert gefunden: avail ID. (HLSManifestResolver)
* Keine Wiedergabesitzung gefunden. (HLSManifestResolver)
* Verarbeitung der VOD-Anfrage für die URL des Manifestinhalts.
* Verarbeitungsvariante.
* Verarbeitungsanfrage für die Manifestinhalt-URL.
* Tracking-Anfrage wird verarbeitet. (VOD)
* Umleitungs-Anzeigenantwort leer. ( VASTStAX)
* Anfordern: URL.
* Gibt eine Fehlerantwort für eine GET-Anfrage zurück, da keine Wiedergabesitzung gefunden wurde. (VOD)
* Gibt eine Fehlerantwort für eine GET-Anfrage aufgrund eines internen Serverfehlers zurück.
* Gibt eine Fehlerantwort für eine GET-Anfrage zurück, in der ein ungültiges Asset angegeben wird: Anzeigen-Anfrage-ID. (VOD)
* Gibt eine Fehlerantwort für eine GET-Anfrage zurück, in der eine ungültige oder leere Gruppen-ID angegeben wird: Gruppen-ID. (VOD)
* Gibt eine Fehlerantwort für eine GET-Anfrage zurück, in der ein Wert für eine ungültige Tracking-Position angegeben wird. (VOD)
* Ausgabe einer Fehlerantwort für eine GET-Anfrage mit ungültiger Syntax - Anforderungs-URL. (Live/VOD)
* Ausgabe einer Fehlerantwort für Anfrage mit nicht unterstützter HTTP-Methode: GET|POST. (Live/VOD)
* Gibt das Manifest aus dem Cache zurück. (VOD)
* Der Server ist überlastet. Fahren Sie ohne Anzeigenzuordnungsanfrage fort. (Variante)
* Beginnen Sie mit der Generierung des Zielmanifests. (HLSManifestResolver)
* Beginn der Generierung des Variantenmanifests aus: Inhalts-URL. (Variante)
* Beginnen Sie mit dem Zuordnen von Anzeigen zu Manifest. (VODHLSResolver)
* Zuordnen der Anzeige bei `HH:MM:SS`: AdPlacement \[adManifestURL= ad Manifest URL, durationSeconds= seconds, ignore= ignore, redirectAd= redirect ad, priority= priority.\] \(HLSManifestResolver\)
* Es können keine Anzeigen aufgrund einer ungültigen pttimeline abgerufen werden. Der Inhalt wurde ohne Anzeigen zurückgegeben. (VOD)
* Anzeigen können nicht abgerufen werden - Inhalt ohne Anzeigen wurde zurückgegeben. (VOD)
* Anzeigenabfrage kann nicht abgerufen werden und es wurde keine Inhalts-URL angegeben. (VOD)
* Gültige URL empfangen. (VOD/Variante)
* Variante M3U8 wurde nicht gefunden. (Variante)

### TRACE_PLAYBACK_PROGRESS-Datensätze {#trace-playback-progress-records}

Der Manifestserver erzeugt solche Datensätze, wenn er während des Workflows für die serverseitige Verfolgung ein Signal über den Wiedergabeleistungsfortschritt erhält. Felder jenseits `TRACE_PLAYBACK_PROGRESS` werden in der in der Tabelle angezeigten Reihenfolge angezeigt, getrennt durch Tabs.

| Feld | Typ | Beschreibung |
|---|---|---|
| status | Zeichenfolge | HTTP-Statuscode |
| Bandbreite | integer | Bandbreite des Streams |
| Pfade | integer | PTS-Zeit im Stream |
| ms_time | integer | Zeit, zu der der Manifestserver die Tracking-URL generiert hat |
| url | Zeichenfolge | Umleitungs-URL |
| **0** header_user_agent | Zeichenfolge | HTTP-Benutzeragenten-Kopfzeile |
| **0** header_dnt | integer | HTTP-do-not-track-Kopfzeile |
| **0** effective_remote_address | Zeichenfolge | IPv4 effektive Remote-Adresse |
| **0** remote_address | Zeichenfolge | IPv4-Remote-Adresse |

**0** Die letzten vier Felder sind optional.

## Streams mit mehreren Bitraten {#multiple-bitrate-streams}

Client-Anforderungen zum Einfügen von Anzeigen geben in der Regel mehr als eine Bitrate in der Wiedergabeliste im M3U8-Format an. Der Manifestserver erzeugt eine neue M3U8-Variantendatei und gibt für jede Bitrate einen separaten M3U8-Link zurück. Außerdem wird eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verknüpfen.

Der Manifestserver verwendet die Informationen in der Bootstrap-URL-Anfrage des Clients, um die Wiedergabeliste für Inhaltsvarianten abzurufen. Es wird eine neue Wiedergabeliste mit Manifestserver-Links zum Inhalt auf der Stream-Ebene generiert. Der Client verwendet diese zum Erstellen von Anzeigeneinfüge-Anfragen. Die Inhaltslinks auf Stream-Ebene des Manifestservers haben das folgende Format:

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/vod**
Der Manifestserver legt diesen Wert auf Grundlage des Wiedergabelistentyps des Inhalts fest: Live/linear (`#EXT-X-PLAYLIST-TYPE:EVENT`) oder VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **publisherAssetID**
Eindeutige Kennung des Herausgebers für den spezifischen Inhalt, der in der Bootstrap-URL-Anfrage angegeben ist.

* **Ausgabedarstellung**
Der Manifestserver legt dies auf der Grundlage der `BANDWIDTH` -Wert des Inhalts-Streams und verwendet ihn, um die Bitrate der Anzeige mit der Bitrate des Inhalts abzugleichen. Die Bitrate der Anzeige kann die Bitrate des Inhalts nur überschreiten, wenn die Anzeigenausgabe mit der niedrigsten Bitrate dies tut.

* **groupID**
Der Manifestserver generiert diesen Wert und verwendet ihn, um sicherzustellen, dass er Anzeigen konsistent platziert, unabhängig davon, für welche Bitratendarstellungen der Client Anzeigen anfordert.

* **base64-kodierte URL des Bitrate-Streams**
Die URL-sichere Basis 64 des Manifestservers kodiert die absolute URL des Inhaltsstreams. Jeder Stream verfügt über eine eigene URL.

* **Abfrageparameter**
Abfrageparameter, die in der Bootstrap-URL-Anfrage angegeben sind.
