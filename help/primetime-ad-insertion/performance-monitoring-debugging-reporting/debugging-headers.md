---
title: Debugging von Kopfzeilen
description: null
translation-type: tm+mt
source-git-commit: 45e5c8e6144adf4a405bde7d8d19505b7ad549e0
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Debugging-Kopfzeilen (X-ADBE-AI-X1) {#debugging-headers}

SSAI sendet HTTP-Header, die zum Sammeln von Informationen und zur Bestimmung der Leistung für Produktionssitzungen im X-ADBE-AI-X1-Header verwendet werden können.

Beispiel-Kopfzeile:
`X-ADBE-AI-X1: 0 1 1594181097704 15126333-5ba9-49b8-a219-4f37e60d259c v 0 1 30 2 1 199 2 185 497 204 104 0 1 0 4`

Die Beschreibung der Felder lautet wie folgt:

| Name | Beschreibung | Beispiel |
|--- |--- |--- |
| isActivePreroll | Ob ein Anzeigenaufruf für die Pre-Roll-Funktion gesendet wurde | 0 |
| isActiveMidroll | Ob ein Anzeigenaufruf für midroll-roll gesendet wurde | 1 |
| Antrags-ID | Interne SAI | 1594181097704 |
| Sitzungs-ID | Sitzungs-ID der Anforderung | 15126333-5ba9-49b8-a219-4f37e60d259c |
| Stream-Typ | u=Variante, l=live, v=vod | v |
| isBootstrap | Ob diese Anforderung ein Bootstrap-Aufruf ist | 0 |
| Anzahl der Werbeunterbrechungen | Gesamtzahl der Werbeunterbrechungen in diesem Manifest | 1 |
| Dauer der Werbeunterbrechung gesamt | Gesamtdauer der Werbeunterbrechung in Sekunden | 30 |
| Anzahl der Anzeigenaufrufe | Anzahl der in dieser Anforderung gesendeten Anzeigenaufrufe | 2 |
| Anzahl der umgeleiteten Anzeigenaufrufe | Anzahl der Umleitungsanrufe, die in dieser Anforderung gesendet werden | 1 |
| Dauer des Anzeigenaufrufs gesamt | Verarbeitungszeit für Anzeigenaufrufe gesamt | 199 |
| Anzeigenanzahl eingefügt | Anzahl der in das Manifest eingefügten Anzeigen | 2 |
| Anforderungszeit des Quellmanifests | Nur Zeit zum Abrufen von Inhalten | 185 |
| Gesamte Anfragezeit | Gesamtzeit, die mit dem Abrufen von Inhalten und Anzeigen verbracht wurde | 497 |
| Abrufen der Anzeigenmanifestzeit (gesamt) | Gesamtzeit zum Abrufen von Anzeigenmanifesten | 204 |
| Abrufen der Anzeigenmanifestabruf-Zeit (aktuell) | Tatsächliche Zeitspanne zum Abrufen von Anzeigen wird parallel angezeigt | 104 |
| Content Cache-Treffer | Anzahl der Treffer im Inhaltscache | 0 |
| Content Cache-Fehler | Anzahl der Inhaltscache-Fehler | 1 |
| Treffer im Anzeigenmanifest-Cache | Anzahl der Cache-Treffer des Anzeigenmanifests | 0 |
| Anzeigenmanifestcache-Fehler | Anzahl der Cache-Fehler im Anzeigenmanifest | 4 |