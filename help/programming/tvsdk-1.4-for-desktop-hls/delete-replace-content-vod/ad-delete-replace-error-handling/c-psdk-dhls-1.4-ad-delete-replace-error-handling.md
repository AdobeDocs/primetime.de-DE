---
description: TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
title: Umgang mit Anzeigenlöschungen und Ersatzfehlern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Umgang mit Anzeigenlöschungen und Ersatzfehlern {#ad-deletion-and-replacement-error-handling}

TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.

TVSDK-Angebote `timeRanges` Fehlern durch standardmäßige Zusammenführung und Neuanordnung. Zunächst werden kundendefinierte Zeiträume nach dem *begin* Zeit. Basierend auf dieser Sortierreihenfolge werden dann benachbarte Bereiche zusammengeführt und miteinander verbunden, wenn es Untergruppen und Schnittmengen zwischen den Bereichen gibt.

TVSDK behandelt Zeitbereichsfehler wie folgt:

* Nicht in der Reihenfolge - TVSDK ordnet die Zeiträume neu an.
* Teilmenge - TVSDK führt die Zeitbereichs-Teilmengen zusammen.
* Schnittmenge - TVSDK führt die sich überschneidenden Zeiträume zusammen.
* Bereichskonflikt ersetzen - TVSDK wählt die Ersetzungsdauer ab dem frühesten angezeigten Zeitpunkt aus `timeRange` in der in Konflikt stehenden Gruppe.

TVSDK behandelt Signalmoduskonflikte wie folgt:

* Wenn Ersatzbereiche definiert sind, ändert TVSDK automatisch den Signalmodus zu CUSTOM_RANGE.
* Wenn DELETE- oder MARK-Bereiche definiert sind und der Signalmodus &quot;CUSTOM_RANGE&quot;lautet, löscht oder markiert TVSDK diese Bereiche. In diesem Fall gibt es keine Anzeigeneinfügung.
* Wenn ein DELETE- oder MARK-Bereich eine Ersatzdauer definiert, ignoriert TVSDK diese Dauer.

Wenn der Server keine Gültigkeit zurückgibt `AdBreaks`:

* TVSDK generiert und verarbeitet eine `NOPTimelineOperation` für leere `AdBreak`. Keine Anzeige wird wiedergegeben.

## Beispiele für Zeitbereichsfehler {#time-range-error-examples}

TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.

Im folgenden Beispiel werden vier sich überschneidende DELETE-Zeitbereiche definiert. TVSDK führt die vier Zeitbereiche zu einem aus, sodass der tatsächliche Löschbereich zwischen 0 und 50 liegt.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000
    }, {
        "begin": 20000,
        "end": 50000
    }, {
        "begin": 0,
        "end": 30000
    }, {
        "begin": 30000,
        "end": 40000
    } ]
}
```

Im folgenden Beispiel werden vier ERSETZUNGS-Zeitbereiche mit widersprüchlichen Zeitbereichen definiert. In diesem Fall ersetzt TVSDK 0-50 durch 25 Anzeigen. Sie wird mit der ersten Ersetzungsdauer in der Sortierreihenfolge aktualisiert, da in nachfolgenden Bereichen Konflikte auftreten.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000,
        "replace-duration": 15000
    }, {
        "begin": 20000,
        "end": 50000,
        "replace-duration": 20000
    }, {
        "begin": 0,
        "end": 30000,
        "replace-duration": 25000
    }, {
        "begin": 30000,
        "end": 40000,
        "replace-duration": 30000
    } ]
}
```
