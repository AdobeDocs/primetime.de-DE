---
title: Besondere Anwendungsfälle
description: Besondere Anwendungsfälle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Besondere Anwendungsfälle{#special-use-cases}

TVSDK bevorzugt benutzerdefinierte Bereichseinstellungen gegenüber den Standardanzeigeneinstellungen. Wenn beispielsweise MARK-Bereiche definiert sind, werden die Einfügeeinstellungen der Anzeige ignoriert. Wenn Ersatzbereiche definiert sind, verwendet TVSDK automatisch die `CustomRanges` Signalmodus.

1. `ReplaceRange` ohne Ersatzdauer

   Wenn die Ersatzdauer fehlt, wird die tatsächliche Ersatzdauer vom Server bestimmt. Die Anzahl der hier platzierten Anzeigen `AdBreak` wird auch vom Server bestimmt.

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

1. MARK- und DELETE-Bereiche mit Ersatzdauer

   Die zusätzliche Ersatzdauer wird ignoriert.
