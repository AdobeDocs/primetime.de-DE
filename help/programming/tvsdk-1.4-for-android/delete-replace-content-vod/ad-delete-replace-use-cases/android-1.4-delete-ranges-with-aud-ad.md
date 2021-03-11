---
description: Sie können TimeRanges zwischen "begin"und "end"in localTime aus der Zeitleiste entfernen.
title: Bereiche löschen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 0%

---


# Bereiche{#delete-ranges} löschen

Sie können TimeRanges zwischen &quot;begin&quot;und &quot;end&quot;in localTime aus der Zeitleiste entfernen.

>[!NOTE]
>
>Wenn Sie nur bestimmte Bereiche aus dem Inhalt entfernen möchten und die Anzeigenzuordnung wie vom Anzeigen-Server definiert verwendet werden muss, erstellen Sie eine `CustomRangeMetadata`-Instanz und geben Sie den Typ als DELETE-Vorgang mit den definierten benutzerdefinierten Bereichen an.

Löschen Sie Bereiche mit einer Adobe Primetime-Anzeige zur Anzeigenentscheidung.

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

