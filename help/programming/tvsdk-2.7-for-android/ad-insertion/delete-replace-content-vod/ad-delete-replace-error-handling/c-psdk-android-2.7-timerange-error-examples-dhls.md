---
description: TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.
title: Beispiele für Zeitbereichsfehler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Beispiele für Zeitbereichsfehler{#time-range-error-examples}

TVSDK reagiert auf fehlerhafte Zeitbereichsspezifikationen, indem die Zeiträume entsprechend zusammengeführt oder ersetzt werden.

**DELETE-Zeitbereich**

Im folgenden Beispiel werden vier sich überschneidende DELETE-Zeitbereiche definiert. TVSDK führt die vier Zeitbereiche zu einem aus, sodass der tatsächliche Löschbereich zwischen 0 und 50 liegt.

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

Im folgenden Beispiel werden vier ERSETZUNGS-Zeitbereiche mit widersprüchlichen Zeitbereichen definiert. In diesem Fall ersetzt TVSDK 0-50 durch 25 Anzeigen. Sie wird mit der ersten Ersetzungsdauer in der Sortierreihenfolge aktualisiert, da in nachfolgenden Bereichen Konflikte auftreten.

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
