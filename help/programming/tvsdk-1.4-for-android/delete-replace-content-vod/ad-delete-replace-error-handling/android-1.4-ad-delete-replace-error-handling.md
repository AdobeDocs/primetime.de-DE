---
description: TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
seo-description: TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
seo-title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
title: Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen
uuid: e2e06f13-9813-4d86-b6fe-3d09f3bdb100
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Verarbeitung von Fehlern beim Löschen und Ersetzen von Anzeigen{#ad-deletion-and-replacement-error-handling}

TVSDK verarbeitet Zeitraumfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.

TVSDK behandelt `timeRanges`-Fehler, indem es die standardmäßige Zusammenführung und Neuanordnung vornimmt. Zuerst sortiert es benutzerdefinierte Zeiträume nach der Zeit *begin*. Basierend auf dieser Sortierreihenfolge werden dann angrenzende Bereiche zusammengeführt und bei Untergruppen und Schnittpunkten zwischen den Bereichen verbunden.

TVSDK verarbeitet Zeitraumfehler wie folgt:

* Nicht in der Reihenfolge - TVSDK ordnet die Zeiträume neu an.
* Untergruppe - TVSDK führt die Teilmengen des Zeitraums zusammen.
* Intersect - TVSDK führt die sich überschneidenden Zeiträume zusammen.
* Konflikt zwischen Ersetzungsbereichen - TVSDK wählt die Ersetzungsdauer aus der frühesten Anzeige von `timeRange` in der konfliktbehafteten Gruppe.

TVSDK behandelt Signalmoduskonflikte mit Anzeigenmetadaten wie folgt:

* Wenn der Anzeigensignalisierungsmodus mit den Zeitraummetadaten in Konflikt steht, haben die Zeitraummetadaten immer Priorität. Wenn beispielsweise der Anzeigensignalisierungsmodus als Serverzuordnung oder Manifesturkunde festgelegt ist und die Anzeigenmetadaten auch Zeitbereiche für das Markieren enthalten, wird das Ergebnis angezeigt, dass die Bereiche markiert sind und keine Anzeigen eingefügt werden.
* Wenn der Signalisierungsmodus für REPLACE-Bereiche als Serverzuordnung oder Manifestzeichen festgelegt ist, werden die Bereiche wie in den REPLACE-Bereichen angegeben ersetzt und es wird keine Anzeige über die Serverzuordnung oder die Manifestzuordnung eingefügt. Siehe [Anzeigensignalisierungsmodus](../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-signaling-mode.md).

Wenn der Server kein gültiges `AdBreaks` zurückgibt:

* TVSDK generiert und verarbeitet ein `NOPTimelineOperation` für das leere `AdBreak`. Es wird keine Anzeige wiedergegeben.

Für Zeiträume mit Live-Streams:

* Obwohl diese Funktion zum Löschen/Ersetzen von C3-Anzeigen nur für VOD unterstützt werden soll, werden Zeitbereiche auch für Live-Streams verarbeitet, wenn sie in den Anzeigenmetadaten angegeben sind.

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
