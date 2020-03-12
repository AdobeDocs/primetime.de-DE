---
description: Sie können Anzeigen in VOD-Inhalte einfügen.
seo-description: Sie können Anzeigen in VOD-Inhalte einfügen.
seo-title: Ersetzen von Zeitbereichen durch eine Anzeige
title: Ersetzen von Zeitbereichen durch eine Anzeige
uuid: 8f09560c-bca3-4662-bc58-6c9cd0892476
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Ersetzen von Zeitbereichen durch eine Anzeige {#replace-time-ranges-with-an-ad}

Sie können Anzeigen in VOD-Inhalte einfügen.

Die `TimeRanges` Werte zwischen `begin` und `end` in `localTime` werden aus der Zeitleiste entfernt. Diese Bereiche werden durch ein `AdBreak` von `begin` bis ersetzt `begin+replaceDuration`. Wenn der Parameter `replacement-duration` nicht vorhanden ist, trifft der Server die Entscheidung für die zurückgegebene Datei `Adbreak`.

>[!TIP]
>
>Sie sollten immer einen `replacement-duration` für benutzerdefinierte Bereiche angeben. Wenn keine Anzeigen dazu bestimmt sind, diesen benutzerdefinierten Bereich zu ersetzen, geben Sie einen `replacement-duration` Wert von 0 an.

1. So ersetzen Sie die Bereiche durch Primetime- und Entscheidungsanzeigen:

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
                   "type": "replace",
                   "time-range-list": [
                       {
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
       "title": "VOD - Replace TimeRange with Auditude Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   }
   ```

