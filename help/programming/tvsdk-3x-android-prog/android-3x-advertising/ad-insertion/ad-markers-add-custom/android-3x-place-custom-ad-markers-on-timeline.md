---
description: In diesem Beispiel wird die empfohlene Methode zum Einschließen benutzerdefinierter Anzeigenmarken in die Wiedergabescheitleiste gezeigt.
title: Platzieren benutzerdefinierter Anzeigenmarkierungen auf der Timeline
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Platzieren benutzerdefinierter Anzeigenmarkierungen auf der Timeline {#place-custom-ad-markers-on-the-timeline}

In diesem Beispiel wird die empfohlene Methode zum Einschließen benutzerdefinierter Anzeigenmarken in die Wiedergabescheitleiste gezeigt.

1. Übersetzen Sie die Out-of-Band-Anzeigenpositionsinformationen in eine Liste/ein Array von `RepaceTimeRange` -Klasse.
1. Erstellen Sie eine Instanz von `CustomRangeMetadata` -Klasse und verwenden Sie ihre `setTimeRangeList` -Methode mit der Liste/dem Array als Argument zum Festlegen der Zeitbereichsliste verwenden.
1. Verwenden Sie seine `setType` -Methode, um den Typ auf `MARK_RANGE`.
1. Verwenden Sie die `MediaPlayerItemConfig.setCustomRangeMetadata` -Methode mit `CustomRangeMetadata` -Instanz als Argument zum Festlegen der benutzerdefinierten Bereichs-Metadaten.
1. Verwenden Sie die `MediaPlayer.replaceCurrentResource` -Methode mit `MediaPlayerItemConfig` -Instanz als Argument verwenden, um die neue Ressource zur aktuellen Ressource zu machen.
1. Warten Sie auf einen `STATE_CHANGED` -Ereignis, das meldet, dass sich der Player im `PREPARED` state.
1. Starten Sie die Videowiedergabe durch Aufruf von `MediaPlayer.play`.

Dies ist das Ergebnis des Abschlusses der Aufgaben in diesem Beispiel:

* Wenn eine `ReplaceTimeRange` überschneidet sich auf der Wiedergabezeitleiste gegenseitig, z. B. die Startposition eines `ReplaceTimeRange` ist früher als eine bereits platzierte Endposition, passt TVSDK den Start der Straftat still an `ReplaceTimeRange` um den Konflikt zu vermeiden.

  Dadurch wird die angepasste `ReplaceTimeRange` kürzer als ursprünglich angegeben. Wenn die Anpassung zu einer Dauer von null führt, senkt TVSDK die Verstöße still `ReplaceTimeRange`.

* TVSDK sucht nach benachbarten Zeitbereichen für benutzerdefinierte Werbeunterbrechungen und fasst sie in separate Werbeunterbrechungen zusammen.

Zeiträume, die nicht an einen anderen Zeitraum angrenzen, werden in Werbeunterbrechungen mit einer einzelnen Anzeige übersetzt.

* Wenn das Programm versucht, eine Medienressource zu laden, deren Konfiguration enthält `CustomRangeMetadata` , die nur in kontextspezifischen Anzeigenmarken verwendet werden können, gibt TVSDK eine Ausnahme aus, wenn das zugrunde liegende Asset nicht vom Typ VOD ist.

* Beim Umgang mit benutzerdefinierten Anzeigenmarken deaktiviert TVSDK andere Mechanismen zur Anzeigenauflösung (z. B. Adobe Primetime-Anzeigenentscheidungen).

  Sie können jedes beliebige TVSDK-Anzeigenauflöser-Modul oder den Mechanismus für benutzerdefinierte Anzeigenmarkierungen verwenden. Wenn Sie benutzerdefinierte Anzeigenmarkierungen verwenden, gilt der Anzeigeninhalt als aufgelöst und wird in der Timeline platziert.

Das folgende Codefragment platziert drei Zeitbereiche auf der Timeline als benutzerdefinierte Anzeigenmarkierungen.

```java
// Assume that the 3 time ranges are obtained through external means 
// Use them to populate the ReplaceTimeRange instance 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 0)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.MARK_RANGE); 
 
//Create a MediaResource instance 
MediaResource mediaResource = MediaResource.createFromUrl( 
        "www.example.com/video/test_video.m3u8", timeRanges.toMedatada(null)); 
 
// Create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// Prepare the content for playback by calling replaceCurrentResource 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentResource(mediaResource, config); 
 
// wait for TVSDK to reach the PREPARED state 
mediaPlayer.addEventListener(MediaPlayerEvent.STATE_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
 
    if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
        // TVSDK is in the PREPARED state, so start the playback  
        mediaPlayer.play(); 
    } 
    ... 
}
```
