---
description: TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
seo-description: TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
seo-title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
uuid: ab153591-0011-44b4-87f9-be0302c2295e
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen {#ad-deletion-and-replacement-error-handling}

TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.

TVSDK behandelt `timeRanges`-Fehler, indem es die standardmäßige Zusammenführung und Neuanordnung vornimmt. Zuerst sortiert es benutzerdefinierte Zeiträume nach der Zeit *begin*. Basierend auf dieser Sortierreihenfolge werden dann angrenzende Bereiche zusammengeführt und bei Untergruppen und Schnittpunkten zwischen den Bereichen verbunden.

TVSDK verarbeitet Zeitraumfehler wie folgt:

* Nicht in der Reihenfolge - TVSDK ordnet die Zeiträume neu an.
* Untergruppe - TVSDK führt die Teilmengen des Zeitraums zusammen.
* Intersect - TVSDK führt die sich überschneidenden Zeiträume zusammen.
* Konflikt zwischen Ersetzungsbereichen - TVSDK wählt die Ersetzungsdauer aus der frühesten Anzeige von `timeRange` in der konfliktbehafteten Gruppe.

TVSDK verarbeitet Signalmoduskonflikte wie folgt:

* Wenn REPLACE-Bereiche definiert sind, ändert TVSDK automatisch den Signalmodus auf CUSTOM_RANGE.
* Wenn DELETE- oder MARK-Bereiche definiert sind und der Signalmodus CUSTOM_RANGE lautet, löscht oder markiert TVSDK diese Bereiche. In diesem Fall gibt es keine Anzeigeneinfügung.
* Wenn ein DELETE- oder MARK-Bereich eine Ersatzdauer definiert, ignoriert TVSDK diese Dauer.

Wenn der Server kein gültiges `AdBreaks` zurückgibt:

* TVSDK generiert und verarbeitet ein `NOPTimelineOperation` für das leere `AdBreak`. Es wird keine Anzeige wiedergegeben.

## Beispiele für Zeitraumfehler {#time-range-error-examples}

TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.

Im folgenden Beispiel werden vier sich überschneidende DELETE-Zeitbereiche definiert. TVSDK führt die vier Zeitbereiche zu einem zusammen, sodass der tatsächliche Löschbereich zwischen 0 und 50 liegt.

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

Im folgenden Beispiel werden vier REPLACE-Zeitbereiche mit miteinander in Konflikt stehenden Zeitbereichen definiert. In diesem Fall ersetzt TVSDK 0-50 durch 25 Anzeigen. Es wird mit der ersten Ersetzungsdauer in der Sortierreihenfolge gewechselt, da es in nachfolgenden Bereichen Konflikte gibt.

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
