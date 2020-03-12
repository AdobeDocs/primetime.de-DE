---
description: 'null'
seo-description: 'null'
seo-title: Spezialanwendungsfälle
title: Spezialanwendungsfälle
uuid: 066bc256-4fdf-4083-b23e-0a916b3b532f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Spezialanwendungsfälle{#special-use-cases}

TVSDK bevorzugt benutzerdefinierte Bereichseinstellungen im Vergleich zu standardmäßigen Anzeigeneinstellungen. Wenn beispielsweise MARK-Bereiche definiert sind, werden die Einfügeeinstellungen der Anzeige ignoriert. Wenn REPLACE-Bereiche definiert sind, verwendet TVSDK automatisch den `CustomRanges` Signalmodus.

1. `ReplaceRange` ohne Ersatzdauer

   Wenn die Ersatzdauer fehlt, wird die tatsächliche Austauschdauer vom Server bestimmt. Die Anzahl der darin platzierten Anzeigen `AdBreak` wird auch vom Server bestimmt.

   ```
   {
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://. . ./vanilla/index.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "signaling-mode": "custom time ranges",
               "time-ranges": {
                   "type": "replace",
                   "adjust-seek-position": true,
                   "time-range-list": [{
                   "begin": 0,
                   "end": 30000
               }, {
                   "begin": 60000,
                   "end": 75000
               }, {
                   "begin": 255000,
                   "end": 300000
               } ]
               },
               "ad": {             
                   "domain": "sandbox2.auditude.com",
                   "mediaid": "psdk_000105",
                   "zoneid": "121781"
               }     
           }
       },
       "title": "Verify 30Sec Pre-Roll, 15 Sec Mid roll Ad and 
       45 second Post-Roll can be replaced in one shot.",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_001"
   }
   ```

1. MARK- und DELETE-Bereiche mit Austauschdauer

   Die zusätzliche Ersetzungsdauer wird ignoriert.
