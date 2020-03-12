---
description: Sie können Anzeigen in VOD-Inhalte einfügen.
seo-description: Sie können Anzeigen in VOD-Inhalte einfügen.
seo-title: Ersetzen von Zeitbereichen durch eine Anzeige
title: Ersetzen von Zeitbereichen durch eine Anzeige
uuid: 50cdcc06-7df5-414b-95d4-c684bc68dce3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Ersetzen von Zeitbereichen durch eine Anzeige{#replace-time-ranges-with-an-ad}

Sie können Anzeigen in VOD-Inhalte einfügen.

In diesem Fall werden `TimeRanges` zwischen `begin` und `end` `localTime` in aus der Zeitleiste entfernt. Sie werden durch ein `AdBreak` von `begin` zu `begin+replaceDuration`ersetzen. Wenn die Ersatzdauer nicht als Parameter vorhanden ist, trifft der Server die Entscheidung für die zurückgegebene Adbreak.

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

