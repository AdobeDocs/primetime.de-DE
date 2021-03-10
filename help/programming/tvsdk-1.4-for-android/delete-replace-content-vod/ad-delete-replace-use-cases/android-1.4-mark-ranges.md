---
description: Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.
title: Markierbereiche
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Markierbereiche{#mark-ranges}

Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.

In diesem Fall wird `TimeRanges` zwischen `begin` und `end` in `localTime` in der Zeitleiste als `AdBreak` markiert. Andere Anzeigeneinstellungen werden ignoriert.

>[!NOTE]
>
>Wenn Sie nur bestimmte Bereiche im Inhalt als Anzeigen markieren möchten (ohne dynamische Anzeigeneinfügung), erstellen Sie eine `CustomRangeMetadata`-Instanz und geben Sie den Typ als MARK-Vorgang mit den definierten benutzerdefinierten Bereichen an.

1. Markierungsbereiche.

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "time-ranges": {
                   "type": "mark",
                   "adjust-seek-position" : true,   
                   "time-range-list": [ {
                       "begin": 0,
                       "end": 15000
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
                    } ]
               }
           }           
       },   
       "title": "VOD - MARK TimeRanges and no ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
          },
       "type": "vod",
       "id": "vod_004"
   }
   ```

