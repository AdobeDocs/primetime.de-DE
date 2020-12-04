---
description: Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.
seo-description: Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.
seo-title: Markierbereiche
title: Markierbereiche
uuid: eb99a1c2-6c0c-40a4-bac2-98dce45acfad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '95'
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

