---
description: Sie können TimeRanges zwischen "begin"und "end"in localTime aus der Zeitleiste entfernen.
seo-description: Sie können TimeRanges zwischen "begin"und "end"in localTime aus der Zeitleiste entfernen.
seo-title: Bereiche löschen
title: Bereiche löschen
uuid: 2f4afa0d-69e3-4929-8dbd-b553c8a64d96
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '94'
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

