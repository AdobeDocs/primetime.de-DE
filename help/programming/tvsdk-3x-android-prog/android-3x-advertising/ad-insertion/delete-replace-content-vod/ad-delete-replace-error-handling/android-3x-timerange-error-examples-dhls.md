---
description: TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.
seo-description: TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.
seo-title: Fehlerbeispiele im Zeitbereich
title: Fehlerbeispiele im Zeitbereich
uuid: 25ac5985-a844-452e-ac95-5006fdf413e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Fehlerbeispiele im Zeitbereich {#time-range-error-examples}

TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.

**DELETE-Zeitbereich**

Im folgenden Beispiel werden vier sich überschneidende DELETE-Zeitbereiche definiert. TVSDK führt die vier Zeitbereiche zu einem zusammen, sodass der tatsächliche Löschbereich zwischen 0 und 50 liegt.

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000
        },
        {
            "begin": 20000,
            "end": 50000
        },
        {
            "begin": 0,
            "end": 30000
        },
        {
            "begin": 30000,
            "end": 40000
        }
    ]
}
```

**ERSETZEN - Zeitbereich**

Im folgenden Beispiel werden vier REPLACE-Zeitbereiche mit miteinander in Konflikt stehenden Zeitbereichen definiert. In diesem Fall ersetzt TVSDK 0-50 durch 25 Anzeigen. Es wird mit der ersten Ersetzungsdauer in der Sortierreihenfolge gewechselt, da es in nachfolgenden Bereichen Konflikte gibt.

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000,
            "replace-duration": 15000
        },
        {
            "begin": 20000,
            "end": 50000,
            "replace-duration": 20000
        },
        {
            "begin": 0,
            "end": 30000,
            "replace-duration": 25000
        },
        {
            "begin": 30000,
            "end": 40000,
            "replace-duration": 30000
        }
    ]
}
```
