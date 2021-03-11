---
description: Das forceflash-Flag in der Quellcode-Liste erzwingt den Flash-Fallback für eine URL. Für diese URL können Sie den Inhalt mit Adobe Flash Player wiedergeben.
title: Erzwingen des Flash-Ausfalls mithilfe der Medienquellen-Liste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

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

