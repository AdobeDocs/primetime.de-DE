---
description: Der Inhalt der vollständigen Ereigniswiedergabe (FER) ist ein in VOD konvertierter Live-Stream, indem das Tag
title: FER-Anzeigenauflösung und -einfügung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# FER-Anzeigenauflösung und -einfügung{#fer-ad-resolving-and-insertion}

Der Inhalt der vollständigen Ereigniswiedergabe (FER) ist ein in VOD konvertierter Live-Stream, indem das Tag #EXT-X-ENDLIST am Ende der Manifestdatei hinzugefügt wird. Der Stream behält seine Anzeigen-Cue-Markierungen bei.

Browser TVSDK behandelt einen FER-Stream als VOD, daher ist der Anzeigesignalmodus standardmäßig `SERVER_MAP`. Da der Stream jedoch seine Anzeigen-Cue-Markierungen behält, können Sie den Anzeigesignalmodus auf `MANIFEST_CUES`, mit dem Sie die Anzeigen-Cue-Markierungen für das Einfügen von Anzeigen verwenden können.

So aktivieren Sie die Anzeigeneinfügung mithilfe von Cue-Markierungen für einen FER-Stream:

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

Das Verhalten zur Auflösung und Einfügung von FER-Anzeigen ähnelt dem Auflösen und Einfügen von Live-Anzeigen. Browser TVSDK führt Folgendes aus:

1. Fügt alle Pre-Roll-Anzeigen am Anfang des Inhalts ein.
1. Löst Anzeigen auf, die durch die im Manifest definierten Cue-Punkte angegeben sind.
1. Ersetzt Teile des Hauptinhalts durch Werbeunterbrechungen gleicher Dauer
1. Berechnet die virtuelle Timeline bei Bedarf neu.

**Einschränkung:** Browser TVSDK unterstützt nur die Wiedergabe von HLS FER-Streams. Außerdem werden MP4-Mid-Roll-Anzeigen in FER-Streams nicht unterstützt.
