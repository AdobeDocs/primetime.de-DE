---
description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
title: Dauer des Videos anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Dauer des Videos anzeigen {#display-the-duration-of-the-video}

Sie können die Dauer des derzeit aktiven Inhalts anzeigen.

Implementieren Sie eine Anzeige mit Videodauer mit dem folgenden Beispielcode:

Die `PTMediaPlayer` Eigenschaft, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)enthält den aktuellen suchbaren Fensterbereich:

* Bei VOD ist dieser Bereich der gesamte VOD-Inhaltsbereich, einschließlich Anzeigen.
* Für live/linear stellt dieser Bereich das suchbare Fenster dar.

Weitere Informationen zur API finden Sie unter [TVSDK 3.4 für iOS-API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v3/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
