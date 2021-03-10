---
title: Spezialanwendungsfälle
description: Spezialanwendungsfälle
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Sonderverwendungsfälle{#special-use-cases}

TVSDK bevorzugt benutzerdefinierte Bereichseinstellungen im Vergleich zu standardmäßigen Anzeigeneinstellungen. Wenn beispielsweise MARK-Bereiche definiert sind, werden die Einfügeeinstellungen der Anzeige ignoriert. Wenn REPLACE-Bereiche definiert sind, verwendet TVSDK automatisch den Signalisierungsmodus `CustomRanges`.

1. `ReplaceRange` ohne Ersatzdauer

   Wenn die Ersatzdauer fehlt, wird die tatsächliche Austauschdauer vom Server bestimmt. Die Anzahl der in diesem `AdBreak` platzierten Anzeigen wird auch vom Server bestimmt.

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
