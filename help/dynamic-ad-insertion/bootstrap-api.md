---
title: Bootstrap-API
description: null
translation-type: tm+mt
source-git-commit: aa43834fea161c537c448b7616c9bd8f779d1a74
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Bootstrap-API {#bootstrap-api}

Erforderliche ParameterErstellen eines Bootstrap

## Parameterbeschreibung {#parameter-description}

| parameter | description | formate |
|---|---|---|
| Pabimode | Aktiviert das Einfügen [von Teilen-Werbeunterbrechungen](ad-insertion-live-linear-stream.md#partial-ad-break-support) für Live-Streams. Mögliche Werte:true, um die Deaktivierung zu aktivieren (Standard deaktiviert) | HLS/DASH |
| ptadwindow | Dauer (in Sekunden) des Lookback-Anzeigenentscheidungsfensters - wie lange Primetime Ad Insertion nach Anzeigen-Hinweisen sucht, wenn ein DVR-Benutzer dem Stream beitritt. Bei einem Wert von null wird die Entscheidung für die Anzeige im anfänglichen Manifest deaktiviert, wobei die Entscheidung erst nach der ersten Aktualisierung fortgesetzt wird. Dieser Parameter ist nützlich, um das Einfügen von Anzeigen in Sitzungen zu deaktivieren, die nur einige Sekunden dauern können (z. B. das Spiegeln von Kanälen). Mögliche Werte:numerische Zeichenfolge 0-1800 (Standard 1800) | Nur HLS |
| ptassetid | Eindeutige ID des Inhalts, der vom Herausgeber zugewiesen und gepflegt wird.  Erforderlich, wenn sie zusammen mit dem Akamai Ad Scaler verwendet werden. | HLS/DASH |
| ptcdn | Liste eines oder mehrerer CDNs zum Hosten transkodierter Assets. Weitere Informationen finden Sie unter [Multi-CDN-Unterstützung](multi-cdn-support.md). Mögliche Werte: akamai, level3, llnw (limelight-Netzwerke), comcastStandardmäßig werden Primetime-Ad Insertion-CDNs verwendet | HLS/DASH |
| ptcueformat | Das angegebene Format der Tags, die für die Anzeigenentscheidung verwendet werden sollen (z. B. Scte35). Mögliche Werte: dpisimple, dpiscte35, elemental Für benutzerdefinierte Cue-Formate wenden Sie sich bitte an Ihren Kundenbetreuer, um den Wert für Ihren Anwendungsfall zu ermitteln. | HLS/DASH |
| ptfailover | Weist den Manifestserver an, Primär- und Failover-Streams zu identifizieren, die in der Übergeordnet-Wiedergabeliste angegeben sind, und sie als Trennsätze zu behandeln. Dies erleichtert Ausfallsicherung und verhindert Zeitfehler. (Nur für Apple HLS-Geräte.) Weitere Informationen finden Sie unter HLS-Player-Switching [erleichtern](hls-switching-to-failover.md) | Nur HLS |
| ptmulticall | Wenn diese Option aktiviert ist, wird für jeden Wert in einem VOD-Asset eine separate Anzeigenanforderung gesendet.  Primetime Ad Insertion versucht standardmäßig, alle Werbeinformationen zu erfassen und sie in einer Anforderung an den Anzeigen-Server zu senden. Mögliche Werte:true, um die Deaktivierung zu aktivieren (Standard deaktiviert) | HLS/DASH |
| pttagds | Aktiviert die Injektion von EXT-X-DISCONTINUITY-SEQUENCE-Tags in HLS-Header.Mögliche Werte:true, um die Deaktivierung zu aktivieren (Standard deaktiviert) | Nur HLS |
| pttimeline | Eine Zeichenfolge, die die gewünschte Zeitschiene für Anzeigenplatzierung und -inhalt enthält, wodurch Werbeunterbrechungen im Inhaltsstream überschrieben werden. [ Siehe VOD-Timeline-Format ] | HLS/DASH |
| pttoken | Aktiviert Content Fragment-/Segmentautorisierungstoken-Schutzsysteme für CDNs Mögliche Werte: akamai, llnw (limelight), ctl (centurylink) (Standard-Tokenisierung ist deaktiviert) | HLS/DASH |
| pttrackingmode | Anzeigenverfolgungssysteme aktivieren:Mögliche Werte:einfach für clientseitige Anzeigenverfolgungsmethoden für serverseitige Anzeigenverfolgungssimplen für die hybride Client/Server-Anzeigenverfolgung (standardmäßig wird keine Anzeigenverfolgung durchgeführt) | HLS/DASH |
| pttrackingversion |  |  |
| ptadtimeout (wie in 20.9.2) |  |  |
| ptparallelstream (wie in 20.9.3) |  |  |
