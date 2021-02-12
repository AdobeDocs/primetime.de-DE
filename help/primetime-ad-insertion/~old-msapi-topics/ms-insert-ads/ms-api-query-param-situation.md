---
description: Neben den Grundparametern für die Abfrage ermöglichen optionale Abfragen, dass der Manifestserver mit verschiedenen Clients und Situationen funktioniert.
seo-description: Neben den Grundparametern für die Abfrage ermöglichen optionale Abfragen, dass der Manifestserver mit verschiedenen Clients und Situationen funktioniert.
seo-title: Optionale Abfragen nach Client und Situation
title: Optionale Abfragen nach Client und Situation
uuid: e3fae41e-9f7d-4f01-9a01-52a1d5f5dad5
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---


# Optionale Abfragen nach Client und Situation {#optional-query-parameters-by-client-and-situation}

Neben den Grundparametern für die Abfrage ermöglichen optionale Abfragen, dass der Manifestserver mit verschiedenen Clients und Situationen funktioniert.

## Anzeigeneinfügung mit Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}

Im Akamai Content Versand-Netzwerk (CDN) fungiert der Akamai Edge-Server als Vermittler zwischen dem Client und dem Manifestserver. Wenn Sie auch die Anzeigenskalierung verwenden, stellen die Parameter `ptassetid` und `live` die erforderlichen Informationen für Akamai Edge bereit.

Der Parameter `ptassetid` ist die ID des Herausgebers für das Asset. Akamai verwendet diese URL anstelle der Base64-kodierten URL, die Sie als Teil der Anforderungs-URL angeben, um die Wiedergabeliste zu identifizieren, die dem Manifestserver zur Anzeigeneinfügung bereitgestellt wird.

Der Parameter `live` unterscheidet zwischen Live-Inhalt und Video On-Demand (VOD). Der Manifestserver benötigt diese Informationen, um seine optimierte Schnittstelle mit Akamai zu unterstützen.

Im Folgenden finden Sie eine Beispiel-URL mit den Parametern für Akamai:

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## Einfügen von Anzeigen aus TVSDK auf Xbox {#section_5DB405F4647240A0B83E72DE35D5EC80}

Ein Player, der auf Primetime TVSDK auf Xbox basiert, muss keine weiteren Parameter für die Abfrage liefern, die über die Basisparameter hinausgehen.

## Einfügen von Anzeigen aus TVSDK unter iOS mit Safari {#section_250E493A125E4F82940D19C7DA2AAB2E}

Ein auf Primetime TVSDK basierender Player unter iOS, der den Safari-Browser verwendet, muss zusätzlich zu den Parametern für die Abfrage die Parameter `ptplayer` und `live` angeben.

Der Manifestserver erkennt den `ptplayer`-Wert `ios-mobileweb` und entfernt den Pre-Roll-Vorgang aus dem zurückgegebenen Anzeigenmanifest.

Der Parameter `live` teilt dem Manifestserver mit, ob Live- oder VOD-Inhalte zurückgegeben werden sollen.

Im Folgenden finden Sie eine Beispiel-URL mit den Parametern für iOS mit Safari:

```URL
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## Anzeigeneinfügung mit einem benutzerdefinierten Anzeigen-Cue-Format {#section_82AF880AAABE4BD4B593D906434D4D89}

Adobe stellt Namen für Ad-Cue-Formate bereit, die sie nicht direkt im Primetime-Paket unterstützt. Um ein solches Format zu verwenden, geben Sie den von der Adobe angegebenen Namen als Wert des Parameters `ptcueformat` an.

Im Folgenden finden Sie eine Beispiel-URL, die ein benutzerdefiniertes Anzeigen-Cue-Format angibt:

```URL
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## Anzeigeneinfügung mithilfe von Anzeigenbezeichnungen, um eine Zeitleiste von FreeWheel für VOD {#section_E0D830F5EEE24639819B975B90F6999F} zu erstellen

Für VOD-Inhalte, die Anzeigenbezeichnungen enthalten, die analysiert und in eine kostenlose Anzeigenanforderung aufgenommen werden sollen, setzen Sie den Wert des Parameters `ptcueformat` auf `DPIsimple`.

Hier eine Beispiel-URL, die die Verwendung einer Zeitleiste von FreeWheel für VOD angibt:

```URL
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## Anzeigeneinfügung mit einer benutzerdefinierten Zeitleiste für VOD {#section_F398F7659164463FA886A4CC787C7B5A}

Damit der Manifestserver entsprechend einer von Ihnen angegebenen Zeitschiene Anzeigen in VOD-Inhalte einfügen kann, setzen Sie den Wert des Parameters `pttimeline` auf eine Zeichenfolge, die die Zeitschiene angibt. Siehe [VOD-Timeline-Format](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md).

Im Folgenden finden Sie eine Beispiel-URL, die eine benutzerdefinierte Zeitschiene für VOD verwendet:

```URL
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

Es gibt einen anfänglichen Umbruch von einer Minute mit bis zu zwei Anzeigen, gefolgt von einem zweiminütigen Inhaltssegment, gefolgt von einem 30-sekündigen Umbruch mit bis zu zwei Anzeigen, gefolgt von einem fünfminütigen Inhaltssegment.

Die Anzeigenzuordnung für eine Zeitleiste für benutzerdefinierten Inhalt für VOD-Inhalte verhält sich wie folgt:

* Die Anzeige wird an der nächstgelegenen Umbruchgrenze nach der vom Anzeigen-Server festgelegten Platzierungszeit angezeigt.

* Segmente sind mindestens zwei Sekunden lang.

## Autorisieren von TS-Segmenten {#section_BF855A4399DC42CB8C0586113A416BBC}

Adobe unterstützt diese Funktion nur für das Akamai-CDN. HTTP Live Streaming (HLS) liefert Transport Stream-(TS-)Segmente mithilfe einer Stream-Level-M3U8-Wiedergabeliste. Mehrere Playlisten auf Stream-Ebene werden dem Client in einer Variante M3U8-Playlist bereitgestellt. Der Client wählt einen Wiedergabelistenstream aus der Liste der Variante aus und lädt dann nacheinander TS-Segmente in dieser Stream-Playlist herunter. Im Normalbetrieb kann der angeforderte Inhalt eine Cookie-Autorisierung erfordern, die vom Manifestserver unsichtbar im Hintergrund verarbeitet wird. Es extrahiert das Cookie aus dem Rohinhalt und hängt ein geeignetes Token an die URL an, die zum Anfordern des ausgewählten Wiedergabelistenstreams verwendet werden soll.

Wenn die Parameter für die Bootstrap-URL-Abfrage `pttoken=true` enthalten, benötigt der Herausgeber ein Cookie, das für die Anforderung jedes TS-Segments verwendet wird, anstatt nur einmal für den gesamten Stream. Der Manifestserver fügt dieses Cookie als Abfrage-Parameter an jede TS-Segment-URL in der Stream-Wiedergabeliste an, die er zurücksendet.
