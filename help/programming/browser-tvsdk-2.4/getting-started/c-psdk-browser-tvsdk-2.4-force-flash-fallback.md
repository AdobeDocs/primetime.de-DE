---
description: Das forceflash-Flag in der Quellcode-Liste erzwingt einen Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player abspielen.
seo-description: Das forceflash-Flag in der Quellcode-Liste erzwingt einen Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player abspielen.
seo-title: Erzwingen der Flash-Ausweichmöglichkeit mithilfe der Media Source-Liste
title: Erzwingen der Flash-Ausweichmöglichkeit mithilfe der Media Source-Liste
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Erzwingen der Flash-Ausweichmöglichkeit mithilfe der Media Source-Liste{#forcing-the-flash-fallback-using-the-media-source-list}

Das forceflash-Flag in der Quellcode-Liste erzwingt einen Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player abspielen.

In der Liste der Medienquelle (z. B. in der `sources.js` Datei) können Sie `forceflash` die Einstellung `true`. Beispiel:

```js
{ 
        "title":"Title of the item listed in the media source list",
        "description":"Description of the item listed in the media source list",
        "isLive":true,
        "content":[ 
            { 
                "format":"HLS",
                "url":"https://path_to_HLS_stream.m3u8"
            },
 
        ],
        "forceflash" : true
},
```

