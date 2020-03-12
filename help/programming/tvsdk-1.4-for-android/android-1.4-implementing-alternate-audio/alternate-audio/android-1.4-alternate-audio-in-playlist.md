---
description: Die Wiedergabeliste für ein Video kann eine unbegrenzte Anzahl alternativer Audiospuren für den Hauptvideoinhalt angeben. Beispielsweise können Sie Ihren Videoinhalten verschiedene Sprachen hinzufügen oder dem Benutzer gestatten, während der Wiedergabe des Inhalts zwischen verschiedenen Spuren auf dem Gerät zu wechseln.
seo-description: Die Wiedergabeliste für ein Video kann eine unbegrenzte Anzahl alternativer Audiospuren für den Hauptvideoinhalt angeben. Beispielsweise können Sie Ihren Videoinhalten verschiedene Sprachen hinzufügen oder dem Benutzer gestatten, während der Wiedergabe des Inhalts zwischen verschiedenen Spuren auf dem Gerät zu wechseln.
seo-title: Alternative Audiospuren in der Wiedergabeliste
title: Alternative Audiospuren in der Wiedergabeliste
uuid: 56720bc8-795d-4a12-ae40-2095d6392666
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Alternative Audiospuren in der Wiedergabeliste{#alternate-audio-tracks-in-the-playlist}

Die Wiedergabeliste für ein Video kann eine unbegrenzte Anzahl alternativer Audiospuren für den Hauptvideoinhalt angeben. Beispielsweise können Sie Ihren Videoinhalten verschiedene Sprachen hinzufügen oder dem Benutzer gestatten, während der Wiedergabe des Inhalts zwischen verschiedenen Spuren auf dem Gerät zu wechseln.

Mit alternativen Audiospuren oder spätgebundenen Audio können Benutzer zwischen mehreren Sprachspuren für HTTP-Video-Streams (live/linear und VOD) wechseln. Sie müssen das Video nicht für jede Audiospur ändern, Duplikat erstellen oder neu verpacken. Sie können mehrere Sprachspuren für ein Video-Asset vor oder nach der ursprünglichen Verpackung des Assets bereitstellen.

>[!TIP]
>
>Damit der alternative Ton mit der Videospur des Hauptmediums gemischt wird, müssen die Zeitstempel der alternativen Spur mit den Zeitstempeln des Tons in der Hauptspur übereinstimmen.

Die Hauptaudiospur ist in der Audiospur mit der `default` Beschriftung enthalten. Metadaten für die alternativen Audio-Streams sind in der Wiedergabeliste in den `#EXT-X-MEDIA` Tags mit `TYPE=AUDIO`.

Beispielsweise könnte ein M3U8-Manifest, das mehrere alternative Audiostreams angibt, wie folgt aussehen:

```
#EXTM3U
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 1",
 AUTOSELECT=YES,DEFAULT=YES
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 2",
 AUTOSELECT=NO,DEFAULT=NO,URI="alternate_audio_aac/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="eng",URI="subtitles/eng/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English (Forced)",DEFAULT=YES,
 AUTOSELECT=YES,FORCED=YES,LANGUAGE="eng",URI="subtitles/eng_forced/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="Français",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="fra",URI="subtitles/fra/prog_index.m3u8"
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=263851,CODECS="mp4a.40.2, avc1.4d400d",
 RESOLUTION=416x234,AUDIO="bipbop_audio",SUBTITLES="subs" 
gear1/prog_index.m3u8
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=577610,CODECS="mp4a.40.2, avc1.4d401e",
 RESOLUTION=640x360,AUDIO="bipbop_audio",SUBTITLES="subs"
gear2/prog_index.m3u8
...
```

