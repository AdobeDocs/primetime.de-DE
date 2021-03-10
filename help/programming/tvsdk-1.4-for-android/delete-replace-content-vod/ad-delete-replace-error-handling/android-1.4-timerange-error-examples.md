---
description: TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.
title: Fehlerbeispiele im Zeitbereich
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Beispiele für Zeitraumfehler{#time-range-error-examples}

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

