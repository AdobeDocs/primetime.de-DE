---
description: Die Wiedergabeliste für ein Video kann eine unbegrenzte Anzahl alternativer Audiospuren für den Hauptvideoinhalt angeben. Beispielsweise können Sie Ihren Videoinhalten verschiedene Sprachen hinzufügen oder dem Benutzer erlauben, während der Wiedergabe des Inhalts zwischen verschiedenen Spuren auf seinem Gerät zu wechseln.
title: Alternative Audiospuren in der Wiedergabeliste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Alternative Audiospuren in der Wiedergabeliste {#alternate-audio-tracks-in-the-playlist}

Die Wiedergabeliste für ein Video kann eine unbegrenzte Anzahl alternativer Audiospuren für den Hauptvideoinhalt angeben. Beispielsweise können Sie Ihren Videoinhalten verschiedene Sprachen hinzufügen oder dem Benutzer erlauben, während der Wiedergabe des Inhalts zwischen verschiedenen Spuren auf seinem Gerät zu wechseln.

Alternative Audiospuren ermöglichen es Benutzern, für HTTP-Videostreams (live/linear und VOD) zwischen mehreren Sprachspuren zu wechseln. Sie müssen das Video nicht für jeden Audiotrack ändern, duplizieren oder neu verpacken. Sie können mehrere Sprachspuren für ein Video-Asset vor oder nach der anfänglichen Verpackung des Assets bereitstellen.

>[!IMPORTANT]
>
>Damit das alternative Audio mit dem Video-Track des Hauptmediums gemischt wird, müssen die Zeitstempel des alternativen Titels mit den Zeitstempeln des Audios im Haupttrack übereinstimmen.

Der Haupt-Audio-Track ist in der Audiospur-Sammlung mit der `default` Beschriftung. Metadaten für die alternativen Audio-Streams sind in der Wiedergabeliste im `#EXT-X-MEDIA` Tags mit `TYPE=AUDIO`.

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
