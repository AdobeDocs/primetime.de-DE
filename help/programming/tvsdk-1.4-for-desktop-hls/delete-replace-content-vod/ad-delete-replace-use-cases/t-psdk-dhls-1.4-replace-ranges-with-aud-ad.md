---
title: Ersetzen von Zeitbereichen durch eine Adobe Primetime-Anzeigenentscheidung
description: Ersetzen von Zeitbereichen durch eine Adobe Primetime-Anzeigenentscheidung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# Ersetzen von Zeitbereichen durch eine Adobe Primetime-Anzeigenentscheidung{#replace-time-ranges-with-an-adobe-primetime-ad-decisioning-ad}

Entfernen `TimeRanges` zwischen `begin` und `end` in `localTime` aus der Timeline. Ersetzen Sie sie durch eine AdBreak von `begin` nach `begin+replaceDuration`.

Ersetzen Sie Bereiche durch Primetime- und Entscheidungsanzeigen.

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": "https://. . ./cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
                    "begin": 0,
                    "end": 15000,
                    "replace-duration": 15000
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
