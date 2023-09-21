---
title: Debugging von Kopfzeilen
description: Debugging von Kopfzeilen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 7%

---

# Debugging-Kopfzeilen (X-ADBE-AI-X1) {#debugging-headers}

SSAI sendet HTTP-Header, die verwendet werden können, um Informationen zu sammeln und die Leistung für Produktionssitzungen zu bestimmen, die sich im Header X-ADBE-AI-X1 befinden.

Beispiel-Kopfzeile:
`X-ADBE-AI-X1: 0 1 1594181097704 15126333-5ba9-49b8-a219-4f37e60d259c v 0 1 30 2 1 199 2 185 497 204 104 0 1 0 4`

Die Beschreibung der Felder lautet wie folgt:

| Name | Beschreibung | Beispiel |
|--- |--- |--- |
| isActivePreroll | Ob ein Anzeigenaufruf für die Pre-Roll gesendet wurde | 0 |
| isActiveMidroll | Gibt an, ob ein Anzeigenaufruf für das Meilenstein-Roll gesendet wurde | 1 |
| Antrags-ID | Interne SSAI | 1594181097704 |
| Sitzungs-ID | Sitzungs-ID der Anfrage | 15126333-5ba9-49b8-a219-4f37e60d259c |
| Streamtyp | u=variant, l=live, v=vod | v |
| isBootstrap | Ob diese Anfrage ein Bootstrap-Aufruf ist | 0 |
| Anzahl der Werbeunterbrechungen | Gesamtzahl der Werbeunterbrechungen in diesem Manifest | 1 |
| Gesamtdauer der Werbeunterbrechung | Gesamtdauer der Werbeunterbrechung in Sekunden | 30 |
| Anzahl der Anzeigenaufrufe | Anzahl der in dieser Anfrage gesendeten Anzeigenaufrufe | 2 |
| Anzahl der Umleitungsanrufe | Anzahl der Umleitungs-Anzeigenaufrufe, die in dieser Anfrage gesendet werden | 1 |
| Gesamtdauer der Anzeigenaufrufe | Verarbeitungszeit für Anzeigenaufrufe gesamt | 199 |
| Anzahl eingefügter Anzeigen | Anzahl der in das Manifest eingefügten Anzeigen | 2 |
| Anforderungszeit des Quellmanifests | Nur zeitlicher Abruf des Inhalts | 185 |
| Gesamte Anforderungsdauer | Gesamtbesuchszeit für das Abrufen von Inhalten und Anzeigen | 497 |
| Abrufzeit des Anzeigenmanifests (gesamt) | Gesamtdauer des Abrufs von Anzeigenmanifesten | 204 |
| Abrufzeit des Anzeigenmanifests (tatsächlich) | Die tatsächliche Zeitdauer, über die die Anzeige abgerufen wird, wird parallel angezeigt | 104 |
| Inhalts-Cache-Treffer | Anzahl der Inhalts-Cache-Treffer | 0 |
| Inhaltscache-Miss | Anzahl der Cache-Fehlschläge im Inhalt | 1 |
| Ad Manifest Cache-Treffer | Anzahl der Cache-Treffer des Anzeigenmanifests | 0 |
| Ad Manifest Cache Miss | Anzahl der Cache-Fehler im Anzeigen-Manifest | 4 |
