---
description: Das forceflash-Flag in der Quellcode-Liste erzwingt den Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player wiedergeben.
seo-description: Das forceflash-Flag in der Quellcode-Liste erzwingt den Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player wiedergeben.
seo-title: Erzwingen des Flash-Ausfalls mithilfe der Medienquellen-Liste
title: Erzwingen des Flash-Ausfalls mithilfe der Medienquellen-Liste
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---


# Erzwingen des Flash-Fallback mithilfe der Medienquellen-Liste{#forcing-the-flash-fallback-using-the-media-source-list}

Das forceflash-Flag in der Quellcode-Liste erzwingt den Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player wiedergeben.

In der Medienquelldatei (z. B. in der Liste `sources.js`) können Sie `forceflash` auf `true` setzen. Beispiel:

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

