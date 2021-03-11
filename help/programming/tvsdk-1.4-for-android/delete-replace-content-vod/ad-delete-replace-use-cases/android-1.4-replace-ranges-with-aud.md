---
description: Sie können Anzeigen in VOD-Inhalte einfügen.
title: Ersetzen von Zeitbereichen durch eine Anzeige
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Ersetzen Sie Zeitbereiche durch eine Anzeige{#replace-time-ranges-with-an-ad}

Sie können Anzeigen in VOD-Inhalte einfügen.

In diesem Fall werden `TimeRanges` zwischen `begin` und `end` in `localTime` aus der Zeitleiste entfernt. Sie werden durch `AdBreak` von `begin` bis `begin+replaceDuration` ersetzt. Wenn die Ersatzdauer nicht als Parameter vorhanden ist, trifft der Server die Entscheidung für die zurückgegebene Adbreak.

>[!NOTE]
>
>Sie sollten immer eine bestimmte Ersetzungsdauer für benutzerdefinierte Bereiche angeben. Wenn keine Anzeigen dazu bestimmt sind, diesen benutzerdefinierten Bereich zu ersetzen, geben Sie eine Ersatzdauer von 0 an.

Ersetzen Sie Bereiche durch Primetime- und Entscheidungsanzeigen.

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": 
              "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
                 
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
                    "begin": 0,
                    "end": 15000,
                    "replacement-duration": 15000 
                },
                {
                    "begin": 69000,
                    "end": 99000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 251000,
                    "end": 281000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 514000,
                    "end": 544000,
                    "replacement-duration": 30000
                } ]
            },
            "ad": {
                "targeting": [ {
                    "value": "MulAdsAvail12346",
                    "key": "osmfKeyMulAdsAvail12346"
                } ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - Replace TimeRange with Auditude Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

