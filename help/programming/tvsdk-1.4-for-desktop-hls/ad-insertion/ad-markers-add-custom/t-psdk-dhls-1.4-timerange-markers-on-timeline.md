---
description: Dieses Beispiel zeigt die empfohlene Methode, um TimeRange-Spezifikationen in die Zeitleiste der Wiedergabe einzubeziehen.
title: Platzieren Sie TimeRange-Anzeigenmarken auf der Zeitleiste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Platzieren Sie TimeRange-Anzeigenmarken auf der Zeitleiste {#place-timerange-ad-markers-on-the-timeline}

Dieses Beispiel zeigt die empfohlene Methode, um TimeRange-Spezifikationen in die Zeitleiste der Wiedergabe einzubeziehen.

1. Übersetzen Sie die Out-of-Band-Positionierungsinformationen in eine Liste der Spezifikationen `TimeRange` (d. h. Instanzen der `TimeRange`-Klasse).
1. Verwenden Sie den Satz der `TimeRange`-Spezifikationen, um eine Instanz der `TimeRangeCollection`-Klasse zu füllen.
1. Übergeben Sie die Metadateninstanz, die von der `TimeRangeCollection`-Instanz abgerufen werden kann, an die `replaceCurrentItem`-Methode (Teil der `MediaPlayer`-Schnittstelle).
1. Warten Sie, bis TVSDK zum Status &quot;VORBEREITT&quot;Transition ist, indem Sie darauf warten, dass der Rückruf `PlaybackEventListener#onPrepared` ausgelöst wird.
1. Beginn-Videowiedergabe durch Aufruf der `play()`-Methode (Teil der `MediaPlayer`-Schnittstelle).

* Umgang mit Zeitleistenkonflikten: Es kann vorkommen, dass sich einige `TimeRange`-Spezifikationen in der Wiedergabedauer überschneiden. Der Wert der Position des Beginns, der einer Spezifikation von `TimeRange` entspricht, kann beispielsweise niedriger sein als der Wert der bereits platzierten Endposition. In diesem Fall passt TVSDK die Position des Beginns der verletzenden `TimeRange`-Spezifikation im Hintergrund an, um Zeitlinienkonflikte zu vermeiden. Durch diese Anpassung wird das neue `TimeRange` kürzer als ursprünglich angegeben. Wenn die Anpassung so extrem ist, dass sie zu einem `TimeRange` mit einer Dauer von null ms führen würde, entfernt TVSDK die verletzende `TimeRange`-Spezifikation leise.

* Wenn `TimeRange`-Spezifikationen für benutzerdefinierte Werbeunterbrechungen bereitgestellt werden, versucht TVSDK, diese in Anzeigen zu übersetzen, die in Werbeunterbrechungen gruppiert sind. TVSDK sucht nach benachbarten `TimeRange` Spezifikationen und gruppiert diese in separate Werbeunterbrechungen. Wenn es Zeiträume gibt, die nicht an einen anderen Zeitraum angrenzen, werden sie in Werbeunterbrechungen mit einer einzigen Anzeige umgewandelt.

* Es wird davon ausgegangen, dass das Medienplayer-Element, das geladen wird, auf ein VOD-Asset verweist. TVSDK überprüft dies, wenn Ihre Anwendung versucht, eine Medienressource zu laden, deren Metadaten `TimeRange`-Spezifikationen enthalten, die nur im Zusammenhang mit der Funktion für benutzerdefinierte Anzeigenmarken verwendet werden können. Wenn das zugrunde liegende Asset nicht VOD ist, löst die TVSDK-Bibliothek eine Ausnahme aus.

* Beim Umgang mit benutzerdefinierten Anzeigenmarken deaktiviert TVSDK andere Anzeigenauflösungsmechanismen (über Adobe Primetime-Anzeigenentscheidungsfunktionen (früher Auditude genannt) oder andere Anzeigenbereitstellungssysteme). Sie können eines der verschiedenen von TVSDK bereitgestellten Anzeigenauflöser-Module oder den benutzerdefinierten Anzeigenmarkierungsmechanismus verwenden. Bei Verwendung der benutzerdefinierten Anzeigen-Marker-API gilt der Anzeigeninhalt als bereits aufgelöst und in der Zeitleiste platziert.

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

Das folgende Codefragment bietet ein einfaches Beispiel, bei dem ein Satz von drei `TimeRange`-Spezifikationen als benutzerdefinierte Anzeigenmarken auf der Zeitleiste platziert werden.

```
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
var timeRanges:TimeRangeCollection = new TimeRangeCollection(); 
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
  
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                             timeRanges.toMetadata(null));
```
