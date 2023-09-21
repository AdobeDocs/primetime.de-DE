---
description: TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.
title: Umgang mit Anzeigenlöschungen und Ersatzfehlern
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Umgang mit Anzeigenlöschungen und Ersatzfehlern{#ad-deletion-and-replacement-error-handling}

TVSDK behandelt Zeitbereichsfehler entsprechend dem jeweiligen Problem, indem die falsch definierten Zeiträume entweder zusammengeführt oder neu angeordnet werden.

TVSDK-Angebote `timeRanges` Fehlern durch standardmäßige Zusammenführung und Neuanordnung. Zunächst werden kundendefinierte Zeiträume nach dem *begin* Zeit. Basierend auf dieser Sortierreihenfolge werden dann benachbarte Bereiche zusammengeführt und miteinander verbunden, wenn es Untergruppen und Schnittmengen zwischen den Bereichen gibt.

TVSDK behandelt Zeitbereichsfehler wie folgt:

* Nicht in der Reihenfolge - TVSDK ordnet die Zeiträume neu an.
* Teilmenge - TVSDK führt die Zeitbereichs-Teilmengen zusammen.
* Schnittmenge - TVSDK führt die sich überschneidenden Zeiträume zusammen.
* Bereichskonflikt ersetzen - TVSDK wählt die Ersetzungsdauer ab dem frühesten angezeigten Zeitpunkt aus `timeRange` in der in Konflikt stehenden Gruppe.

TVSDK behandelt Signalmoduskonflikte mit Anzeigenmetadaten wie folgt:

* Wenn der Anzeigenanzeigemodus mit den Zeitbereichs-Metadaten in Konflikt steht, haben die Zeitbereichsmetadaten immer Priorität. Wenn beispielsweise der Anzeigenanzeigemodus als Server-Mapping- oder Manifestangaben festgelegt ist und die Anzeigenmetadaten auch Zeitbereiche vom Typ &quot;MÄRK&quot;enthalten, wird das resultierende Verhalten dadurch verursacht, dass die Bereiche markiert sind und keine Anzeigen eingefügt werden.
* Wenn der Signalmodus für Ersetzungsbereiche als Server-Mapping- oder Manifestangaben festgelegt ist, werden die Bereiche wie in den Ersetzen-Bereichen angegeben ersetzt und es wird keine Anzeige über Server-Maps oder Manifestanzeigen eingefügt. Siehe [Anzeigenanzeigemodus](../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-signaling-mode.md).

Wenn der Server keine Gültigkeit zurückgibt `AdBreaks`:

* TVSDK generiert und verarbeitet eine `NOPTimelineOperation` für leere `AdBreak`. Keine Anzeige wird wiedergegeben.

Für Zeiträume mit Live-Streams:

* Obwohl diese C3-Funktion zum Löschen/Ersetzen von Anzeigen nur für VOD unterstützt werden soll, werden auch Zeitbereiche für Live-Streams verarbeitet, sofern in den Anzeigenmetadaten angegeben.

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
