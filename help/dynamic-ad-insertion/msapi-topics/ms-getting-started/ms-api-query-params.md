---
description: Die Parameter für die Abfrage geben dem Manifestserver an, welche Art von Client die Anforderung gesendet hat und was dieser Client vom Manifestserver tun möchte. Einige sind erforderlich, andere weisen bestimmte akzeptable Formate oder Werte auf.
seo-description: Die Parameter für die Abfrage geben dem Manifestserver an, welche Art von Client die Anforderung gesendet hat und was dieser Client vom Manifestserver tun möchte. Einige sind erforderlich, andere weisen bestimmte akzeptable Formate oder Werte auf.
seo-title: Manifestserver-Abfrage
title: Manifestserver-Abfrage
uuid: 03632da3-ae20-427c-bd24-4794ab627cc8
translation-type: tm+mt
source-git-commit: 6d25fc11bc4ca91556cae0b944322cd224c89fb5
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# Manifestserver-Abfrage {#manifest-server-query-parameters}

Die Parameter für die Abfrage geben dem Manifestserver an, welche Art von Client die Anforderung gesendet hat und was dieser Client vom Manifestserver tun möchte. Einige sind erforderlich, andere weisen bestimmte akzeptable Formate oder Werte auf.

Die vollständige URL besteht aus der Basis-URL gefolgt von einem Fragezeichen und anschließend `parameterName=value` Argumenten, die durch ein kaufmännisches Und getrennt sind: `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

## Erkannte Parameter {#recognized-parameters}

Der Manifestserver erkennt die folgenden Parameter. Er verarbeitet sie oder übergibt sie zusammen mit allen nicht erkannten Parametern an den Anzeigen-Server.

| Schlüssel | Beschreibung | Erforderlich | Gültige Werte |
|--- |--- |--- |--- |
| `__sid__` | Eindeutige ID, die der Manifestserver zum Generieren der Sitzungs-ID verwendet. | Ja | Alphanumerisch |
| g | Client-Gerätetyp | Wenn Targeting-Regeln vom Gerätetyp abhängen | Siehe Liste unter [Clienttypen](https://adobeprimetime.zendesk.com) (Zendesk-Zugriff erforderlich) |
| k | Suchbegriffe für benutzerdefiniertes Anzeigen-Targeting | Nein | URL-sichere Zeichenfolge im Format Schlüssel1=Wert1;Schlüssel2=Wert2;. . . |
| u | Asset-ID für Primetime-Anzeige einfügen | Ja | MD5-Hash-Wert |
| z | Primetime-Einfügezone-ID für das Asset. | Ja | Integer |
| enableC3 | Der Client befindet sich in einem C3-Fenster. Wenn &quot;true&quot;, ersetzen Sie nur lokale Verfügbarkeiten. Ersetzen Sie andernfalls alle verfügbaren Elemente. | Nein | Boolesch |
| live | Gibt an, ob der Inhalt ein Live- oder VOD-Stream (Video On-Demand) ist. | Akamai Ad Scaler- oder iOS Safari-Client | Boolesch |
| Pabimode | [Unterstützung für das Einfügen](../../msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) von Werbeunterbrechungen aktivieren Bei true oder Beginn deaktivieren bei false | Nein (Standard ist deaktiviert) | beginn , true oder false |
| ptadwindow | Dauer (Sekunden) des Anzeigenverbindungsfensters: Rückblick auf die Suche nach Anzeigen, wenn ein DVR-Benutzer dem Stream beitritt. | Nein (Standard = 1800) | 0 bis 1800 |
| ptassetid | Eindeutige ID des Inhalts, der vom Herausgeber zugewiesen und gepflegt wird. | Akamai Ad Scaler | URL-sichere Zeichenfolge |
| ptcdn | Liste eines oder mehrerer CDNs zum Hosten transkodierter Assets. Siehe [Multi-CDN-Unterstützung](../../creative-repackaging-service/multi-cdn-supportt.md). | Nein (Standard=Akamai) | Beispiel: Akamai, Level3, Limelight, Comcast |
| ptcueformat | Der Name des benutzerdefinierten Ad-Cue-Formats im M3U8. | Nein | DPISimple, DPIScte35, Elemental, NBC, NFL oder Turner |
| ptfailover | Weist den Manifestserver an, Primär- und Failover-Streams zu identifizieren, die in der Übergeordnet-Wiedergabeliste angegeben sind, und sie als Trennsätze zu behandeln. Dies erleichtert Ausfallsicherung und verhindert Zeitfehler. (Nur für Apple HLS-Geräte.) Siehe [Erleichterung des HLS-Player-Switching](../../msapi-topics/ms-insert-ads/hls-switching-to-failover.md) . | Nein | true |
| ptmulticall | Bei der Einstellung true werden mehrere Auditude-Anzeigenaufrufe für FER durchgeführt. eine für jede Werbeunterbrechung.  Wenn &quot;false&quot;fehlt oder auf &quot;false&quot;gesetzt ist, wird ein Anzeigenaufruf an die Auditude für FER gesendet. | Nein | Boolescher Hinweis:  Folgende Anforderungen: <ul><li>ptcueformat-Parameter muss auf nbc eingestellt sein</li><li>Der Parameter pttimeline wird ignoriert.</li></ul> |
| ptplayer | Spieler, der die Anforderung abgibt. | iOS/Safari | ios-mobileweb |
| Darstellung | Automatisch durch Anzeigeneinfügung generiert und von Akamai verwendet. Nicht hinzufügen oder entfernen. | Akamai Ad Scaler |  |
| pttagds | [EXT-X- DISCONTINUITY- SEQUENCE](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3) -Tags aktivieren | Nein | true - Der Manifestserver enthält vor dem Inhalt jeder gesendeten m3u8-Datei ein Sequenztag. Wenn der Parameter nicht vorhanden oder nicht &quot;true&quot;ist, enthält der Manifestserver kein Sequenz-Tag. |
| pttimeline | Eine Zeichenfolge, die die gewünschte Zeitschiene für Anzeigenplatzierung und -inhalt enthält, wodurch Werbeunterbrechungen im Inhaltsstream überschrieben werden. | Nein | VOD-Timeline (siehe [VOD-Timeline-Format](../../msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)) |
| pttoken | Token für die Segmentautorisierung aktivieren Hinweis:  Nur Akamai-CDN-Token werden unterstützt | Für TS-Segmentautorisierungstoken | Boolesch |
| pttrackingmode | Anzeigenverfolgung aktivieren; entweder kundenseitig (einfach), serverseitig (sstm) oder hybrid (simplesstm). | Nein | simple , sstm oder simplesstm Hinweis:  Wenn dieser Parameter nicht enthalten ist, wird der Parameter #EX-X-MARKER in das Manifest eingefügt. Siehe [EXT-X-MARKER-Richtlinie](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md). |
| pttrackingposition | Weist den Manifestserver an, nur Anzeigenverfolgungsinformationen zurückzugeben. Geben Sie diesen Parameter nicht in der Bootstrap-Anforderung an. | Clientseitige Verfolgung | Alphanumerische Anmerkung:  Der Manifestserver ignoriert alle übergebenen Werte. Wenn Sie jedoch eine Null- oder leere Zeichenfolge übergeben, gibt der Manifestserver die M3U8 anstelle der Verfolgungsinformationen zurück. |
| pttrackingversion | Die Formatversion der clientseitigen Verfolgungsinformationen. | Clientseitige Verfolgung | v1, v2, v3 oder vmap |
| scteTracking | Rufen Sie M3U8 ab, bevor Sie SCTE-Verfolgungsinformationen in JSON V2 Sidecar abrufen können.  <br/>Dieser Parameter gibt dem Manifestserver an, dass der Player, der das M3U8 abruft, SCTE-Tag-Informationen abrufen muss. | Nein (Standard:  false ) | true oder false Hinweis:  Die SCTE-35-Daten werden im JSON-Sidecar mit der folgenden Kombination von Abfrage-Parameterwerten zurückgegeben: <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35` </li><li>pttrackingversion=v2 </li><li>scteTracking=true</li></ul> |
| vetargetmultiplier | Die Anzahl der Segmente vom Live-Point Der Pre-Roll-Offset wird wie folgt konfiguriert:   `(  vetargetmultiplier  *  targetduration ) +  vebufferlength`  <br/><br/>**Hinweis**:  Nur Live/Linear | Nein (Standard:  3.0 ) | Float |
| vebufferLength | Die Anzahl Sekunden ab dem Live-Point Hinweis:  Nur Live/Linear | Nein (Standard:  3.0 ) | Float |
| ptadtimeout | Zur Begrenzung der gesamten Anzeigenauflösungszeit, wenn die Reaktion der Anbieter zu lange dauert. | Ja, um | Wert in Millisekunde |
| ptparallelstream | Ermöglicht Kunden mit Playern, die parallel CMAF-demuxed Audio- oder Videostreams anfordern, um sicherzustellen, dass Anzeigen in Audio- und Videospuren konsistent sind. | Ja, um die Funktion zu aktivieren oder die Deaktivierung zu unterlassen. | true |
