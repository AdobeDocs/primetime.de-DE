---
description: Sie können "TimeRanges"zwischen Beginn und Ende in localTime aus der Timeline entfernen.
title: Löschen von Bereichen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 0%

---

# Löschen von Bereichen{#delete-ranges}

Sie können &quot;TimeRanges&quot;zwischen Beginn und Ende in localTime aus der Timeline entfernen.

>[!NOTE]
>
>Wenn Sie nur bestimmte Bereiche aus dem Inhalt entfernen möchten und die Anzeigenzuordnung wie vom Anzeigen-Server definiert verwendet werden muss, erstellen Sie eine `CustomRangeMetadata` und geben Sie den Typ als DELETE-Vorgang mit den definierten benutzerdefinierten Bereichen an.

Löschen von Bereichen mit einer Adobe Primetime-Anzeigenentscheidung.

```
{   
    "properties": [],
    "stream": {
        "manifests": [
            {
                "url": "https://xyz.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                "type": "hls"
            }
        ],
     
        "metadata": {
            "time-ranges": {
                "type": "delete",
                "time-range-list": [
                    {
                        "begin": 0,
                        "end": 20000
                    },
                    {
                        "begin": 69000,
                        "end": 99000
                    },
                    {
                        "begin": 251000,
                        "end": 281000
                    },
                    {
                        "begin": 514000,
                        "end": 544000
                    }
                ]
     
            },
            "ad": {
                "targeting": [
                    {
                        "value": "MulAdsAvail12346",
                        "key": "osmfKeyMulAdsAvail12346"
                    }
                ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - DELETE TimeRange with Primetime ad decisioning Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```
