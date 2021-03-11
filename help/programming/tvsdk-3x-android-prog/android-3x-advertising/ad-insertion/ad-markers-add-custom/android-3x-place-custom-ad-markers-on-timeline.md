---
description: In diesem Beispiel wird die empfohlene Möglichkeit veranschaulicht, benutzerdefinierte Anzeigenmarken in die Zeitleiste der Wiedergabe einzubeziehen.
title: Platzieren benutzerdefinierter Anzeigenmarken auf der Zeitleiste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Platzieren Sie benutzerdefinierte Anzeigenmarken auf der Zeitleiste {#place-custom-ad-markers-on-the-timeline}

In diesem Beispiel wird die empfohlene Möglichkeit veranschaulicht, benutzerdefinierte Anzeigenmarken in die Zeitleiste der Wiedergabe einzubeziehen.

1. Übersetzen Sie die Out-of-Band-Positionierungsinformationen in eine Liste/ein Array der `RepaceTimeRange`-Klasse.
1. Erstellen Sie eine Instanz der Klasse `CustomRangeMetadata` und verwenden Sie die `setTimeRangeList`-Methode mit der Liste/dem Array als Argument, um die Liste des Zeitraums festzulegen.
1. Verwenden Sie die `setType`-Methode, um den Typ auf `MARK_RANGE` einzustellen.
1. Verwenden Sie die `MediaPlayerItemConfig.setCustomRangeMetadata`-Methode mit der `CustomRangeMetadata`-Instanz als Argument, um die Metadaten für den benutzerdefinierten Bereich festzulegen.
1. Verwenden Sie die `MediaPlayer.replaceCurrentResource`-Methode mit der `MediaPlayerItemConfig`-Instanz als Argument, um die neue Ressource als aktuelle Ressource festzulegen.
1. Warten Sie auf ein `STATE_CHANGED`-Ereignis, das meldet, dass sich der Player im Status `PREPARED` befindet.
1. Beginn-Videowiedergabe durch Aufruf von `MediaPlayer.play`.

Im Folgenden finden Sie das Ergebnis des Abschlusses der Aufgaben in diesem Beispiel:

* Wenn ein `ReplaceTimeRange` einen anderen Bereich in der Wiedergabeschlüssel überschneidet, z. B. wenn die Position des Beginns eines `ReplaceTimeRange` vor einer bereits platzierten Endposition liegt, passt TVSDK den Beginn des beleidigenden `ReplaceTimeRange`-Werts im Hintergrund an, um den Konflikt zu vermeiden.

   Dadurch wird das angepasste `ReplaceTimeRange` kürzer als ursprünglich angegeben. Führt die Anpassung zu einer Dauer von null, senkt TVSDK die verletzenden &lt; a0/> im Hintergrund.`ReplaceTimeRange`

* TVSDK sucht nach angrenzenden Zeitbereichen für benutzerdefinierte Werbeunterbrechungen und gruppiert diese in separate Werbeunterbrechungen.

Zeiträume, die nicht an einen anderen Zeitraum angrenzen, werden in Werbeunterbrechungen mit einer einzigen Anzeige umgewandelt.

* Wenn die Anwendung versucht, eine Medienressource zu laden, deren Konfiguration `CustomRangeMetadata` enthält, die nur im Kontext von benutzerdefinierten Anzeigenmarken verwendet werden kann, löst TVSDK eine Ausnahme aus, wenn das zugrunde liegende Asset nicht VOD ist.

* Beim Umgang mit benutzerdefinierten Anzeigenmarken deaktiviert TVSDK andere Mechanismen zur Anzeigenauflösung (z. B. Adobe Primetime-Anzeigenentscheidung).

   Sie können ein beliebiges TVSDK-Anzeigenauflöser-Modul oder den benutzerdefinierten Anzeigenmarkierungsmechanismus verwenden. Wenn Sie benutzerdefinierte Anzeigenmarken verwenden, wird der Anzeigeninhalt als aufgelöst betrachtet und auf der Zeitleiste platziert.

Im folgenden Codefragment werden drei Zeitbereiche auf der Zeitleiste als benutzerdefinierte Anzeigenmarken platziert.

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
