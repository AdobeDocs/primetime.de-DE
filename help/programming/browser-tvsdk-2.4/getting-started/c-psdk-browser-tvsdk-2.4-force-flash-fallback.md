---
description: Das erzwungene Flash-Flag in der Quellliste erzwingt das Flash-Fallback für eine URL. Für diese URL können Sie Adobe-Flash Player verwenden, um den Inhalt abzuspielen.
title: Erzwingen des Flash-Fallback mithilfe der Medienquellenliste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Erzwingen des Flash-Fallback mithilfe der Medienquellenliste{#forcing-the-flash-fallback-using-the-media-source-list}

Das erzwungene Flash-Flag in der Quellliste erzwingt das Flash-Fallback für eine URL. Für diese URL können Sie Adobe-Flash Player verwenden, um den Inhalt abzuspielen.

In der Liste der Medienquellen (z. B. in der `sources.js` Datei), können Sie `forceflash` nach `true`. Beispiel:

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
