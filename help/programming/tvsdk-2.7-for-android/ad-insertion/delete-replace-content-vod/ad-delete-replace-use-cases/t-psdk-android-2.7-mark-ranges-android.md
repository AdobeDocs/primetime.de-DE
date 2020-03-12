---
description: Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.
seo-description: Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.
seo-title: Markierbereiche
title: Markierbereiche
uuid: 6ae2adee-fb7a-4cef-a8e8-ecf671ed3660
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Markierbereiche {#mark-ranges}

Sie können Zeitintervalle im VOD-Inhalt als Werbeunterbrechungen festlegen.

Die `TimeRanges` Werte zwischen `begin` und `end` in `localTime` werden in der Zeitleiste als `AdBreak` eine markiert. Andere Anzeigeneinstellungen werden ignoriert.

>[!TIP]
>
>Wenn Sie nur bestimmte Bereiche des Inhalts ohne dynamische Anzeigeneinfügung als Anzeigen markieren möchten, erstellen Sie eine `CustomRangeMetadata` Instanz und geben Sie den Typ als `MARK` Vorgang mit den definierten benutzerdefinierten Bereichen an.

1. Markieren Sie die Bereiche:

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [
               {
                   "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                   "type": "hls"
               }
           ],
   
       "metadata": {
           "time-ranges": {
                   "type": "mark",
               "adjust-seek-position" : true,   
                   "time-range-list": [
                     {
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
                       }
                    ]
   
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

