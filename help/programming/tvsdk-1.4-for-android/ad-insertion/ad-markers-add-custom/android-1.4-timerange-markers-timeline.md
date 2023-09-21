---
description: In diesem Beispiel wird die empfohlene Methode zum Einbeziehen von TimeRange-Spezifikationen in die Wiedergabe-Timeline veranschaulicht.
title: Platzieren von TimeRange-Anzeigenmarkierungen auf der Timeline
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Platzieren von TimeRange-Anzeigenmarkierungen auf der Timeline {#place-timerange-ad-markers-on-the-timeline}

In diesem Beispiel wird die empfohlene Methode zum Einbeziehen von TimeRange-Spezifikationen in die Wiedergabe-Timeline veranschaulicht.

1. Übersetzen Sie die Out-of-Band-Anzeigenpositionsinformationen in eine Liste von `TimeRange` Spezifikationen (also Instanzen der `TimeRange` -Klasse).
1. Verwenden Sie die `TimeRange` Spezifikationen zum Ausfüllen einer Instanz der `TimeRangeCollection` -Klasse.
1. Übergeben Sie die Metadateninstanz, die aus dem `TimeRangeCollection` -Instanz, um `replaceCurrentItem` -Methode (Teil der MediaPlayer-Schnittstelle).
1. Warten Sie, bis TVSDK zum `PREPARED` state durch Warten auf `PlaybackEventListener#onPrepared` Callback auszulösen.
1. Starten Sie die Videowiedergabe, indem Sie `play()` -Methode (Teil der `MediaPlayer` -Schnittstelle).

* Umgang mit Timeline-Konflikten: Es kann in einigen Fällen vorkommen, in denen `TimeRange` Spezifikationen überschneiden sich auf der Wiedergabescheitleiste. Beispielsweise der Wert der Startposition, der einem `TimeRange` Die Spezifikation kann unter dem Wert der Endposition liegen, die bereits platziert wurde. In diesem Fall passt TVSDK die Startposition der Straftat still an `TimeRange` -Spezifikation, um Zeitleistenkonflikte zu vermeiden. Durch diese Anpassung wird die neue `TimeRange` kürzer als ursprünglich angegeben ist. Wenn die Anpassung so extrem ist, dass sie zu einer `TimeRange` mit einer Dauer von null ms, senkt TVSDK still die Straftat `TimeRange` Spezifikation.
* Wann `TimeRange` Spezifikationen für benutzerdefinierte Werbeunterbrechungen bereitgestellt werden, versucht TVSDK, diese in Anzeigen zu übersetzen, die in Werbeunterbrechungen gruppiert sind. TVSDK sucht nach dem benachbarten `TimeRange` -Spezifikationen und fasst sie in separate Werbeunterbrechungen zusammen. Wenn es Zeiträume gibt, die nicht an einen anderen Zeitraum angrenzen, werden sie in Werbeunterbrechungen mit einer einzelnen Anzeige übersetzt.
* Es wird davon ausgegangen, dass das Medienplayer-Element, das geladen wird, auf ein VOD-Asset verweist. TVSDK überprüft dies jedes Mal, wenn Ihre Anwendung versucht, eine Medienressource zu laden, deren Metadaten enthalten `TimeRange` -Spezifikationen, die nur im Kontext der benutzerdefinierten Anzeigenmarkierungsfunktion verwendet werden können. Wenn das zugrunde liegende Asset nicht vom Typ VOD ist, löst die TVSDK-Bibliothek eine Ausnahme aus.
* Beim Umgang mit benutzerdefinierten Anzeigenmarken deaktiviert TVSDK andere Mechanismen zur Anzeigenauflösung (über Adobe Primetime-Anzeigenentscheidungen (früher als Auditude bezeichnet) oder ein anderes Anzeigenbereitstellungssystem). Sie können eines der verschiedenen von TVSDK bereitgestellten Anzeigenauflöser-Module oder den benutzerdefinierten Anzeigenmarkierungsmechanismus verwenden. Bei Verwendung der benutzerdefinierten Anzeigen-Marker-API gilt der Anzeigeninhalt als bereits aufgelöst und in der Timeline platziert.

Das folgende Codefragment bietet ein einfaches Beispiel, bei dem eine Reihe von drei TimeRange-Spezifikationen als benutzerdefinierte Anzeigenmarkierungen auf der Timeline platziert werden.

```java>
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
TimeRangeCollection timeRanges = new TimeRangeCollection();  
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
 
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                               timeRanges.toMetadata(null)); 
 
// prepare the content for playback by creating 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentItem(mediaResource); 
// wait for TVSDK to reach the PREPARED state 
... 
MediaPlayer.PlaybackEventListener playbackEventListener = new 
  MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // TVSDK in in the PREPARED state. We are allowed to start the playback  
        mediaPlayer.play(); 
    } 
} 
```
