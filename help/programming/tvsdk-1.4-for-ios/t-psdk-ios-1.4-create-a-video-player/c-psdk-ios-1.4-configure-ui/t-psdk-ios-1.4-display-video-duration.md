---
description: Sie können die Dauer des derzeit aktiven Inhalts anzeigen.
title: Dauer des Videos anzeigen
exl-id: 4e31d784-4d16-470b-8317-11be32a55c2f
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Dauer des Videos anzeigen {#display-the-duration-of-the-video}

Sie können die Dauer des derzeit aktiven Inhalts anzeigen.

Implementieren Sie eine Anzeige mit Videodauer mit dem folgenden Beispielcode:

Die `PTMediaPlayer` Eigenschaft, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)enthält den aktuellen suchbaren Fensterbereich:

* Bei VOD ist dieser Bereich der gesamte VOD-Inhaltsbereich, einschließlich Anzeigen.
* Für live/linear stellt dieser Bereich das suchbare Fenster dar.

Weitere Informationen zur API finden Sie unter [TVSDK 1.4 für iOS-API-Referenz](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
