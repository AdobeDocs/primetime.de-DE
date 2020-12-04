---
description: 'Vollständiger Ereignis-Replay-Inhalt (FER) ist ein Live-Stream, der in VOD konvertiert wird, indem das Tag #EXT-X-ENDLIST am Ende der Manifestdatei hinzugefügt wird. Der Stream behält seine Anzeigen-Cue-Marker bei.'
seo-description: 'Vollständiger Ereignis-Replay-Inhalt (FER) ist ein Live-Stream, der in VOD konvertiert wird, indem das Tag #EXT-X-ENDLIST am Ende der Manifestdatei hinzugefügt wird. Der Stream behält seine Anzeigen-Cue-Marker bei.'
seo-title: FER-Anzeigenauflösung und -einfügung
title: FER-Anzeigenauflösung und -einfügung
uuid: 85da0e92-17fe-4001-a53c-085dadd09756
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# FER-Anzeigen lösen und einfügen{#fer-ad-resolving-and-insertion}

Vollständiger Ereignis-Replay-Inhalt (FER) ist ein Live-Stream, der in VOD konvertiert wird, indem das Tag #EXT-X-ENDLIST am Ende der Manifestdatei hinzugefügt wird. Der Stream behält seine Anzeigen-Cue-Marker bei.

Browser TVSDK behandelt einen FER-Stream als VOD, daher ist der Anzeigensignalisierungsmodus standardmäßig `SERVER_MAP`. Da der Stream jedoch seine Anzeigen-Cue-Marker beibehält, können Sie den Anzeigensignalisierungsmodus auf `MANIFEST_CUES` einstellen, sodass Sie die Anzeigen-Cue-Marker für das Einfügen von Anzeigen verwenden können.

So aktivieren Sie die Anzeigeneinfügung mithilfe von Cue-Markierungen für einen FER-Stream:

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

Das Auflösen und Einfügen von FER-Anzeigen ähnelt dem Auflösen und Einfügen von Live-Anzeigen. Browser TVSDK führt Folgendes aus:

1. Fügt alle Pre-Roll-Anzeigen am Anfang des Inhalts ein.
1. Löst Anzeigen auf, die von den im Manifest definierten Cue-Points angegeben wurden.
1. Ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer
1. Berechnet die virtuelle Zeitleiste bei Bedarf neu.

**Einschränkung:** Browser TVSDK unterstützt nur die Wiedergabe von HLS FER-Streams. Außerdem werden MP4-Mid-Roll-Anzeigen für FER-Streams nicht unterstützt.
