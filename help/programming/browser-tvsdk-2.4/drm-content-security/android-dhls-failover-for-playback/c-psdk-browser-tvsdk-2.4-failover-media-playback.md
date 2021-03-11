---
description: Bei Live- und VOD-Beginn wird die Wiedergabe von Browser TVSDK durch Herunterladen der Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, und Herunterladen von Segmenten der Bitratenmedien mit mittlerer Auflösung, die von der Wiedergabeliste definiert werden, gestartet.
title: Medienwiedergabe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# Medienwiedergabe {#media-playback}

Bei Live- und VOD-Beginn wird die Wiedergabe von Browser TVSDK durch Herunterladen der Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, und Herunterladen von Segmenten der Bitratenmedien mit mittlerer Auflösung, die von der Wiedergabeliste definiert werden, gestartet.

Browser TVSDK wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.

## Fehlendes Playlist-Failover {#section_81A5822C108449E1A0E94A6E25DE9E8E}

Wenn eine vollständige Wiedergabeliste fehlt, z. B. wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht Browser TVSDK eine Wiederherstellung. Wenn der Vorgang nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate mit mittlerer Auflösung verknüpft ist, fehlt, sucht Browser TVSDK nach einer VariantenWiedergabeliste mit derselben Auflösung. Wenn die gleiche Auflösung gefunden wird, werden die Variantenplaylist und die Segmente von der entsprechenden Position heruntergeladen. Wenn Browser TVSDK nicht dieselbe Auflösungs-Playlist findet, wird versucht, durch andere Bitrate-Playlisten und deren Varianten zu blättern. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann die Variante usw. Wenn alle Playlisten mit niedrigeren Bitraten und ihre Varianten erschöpft sind, um eine gültige Playlist zu finden, wird Browser TVSDK zur obersten Bitrate gehen und von dort aus zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt zum FEHLER-Status.

Ihre Anwendung kann bestimmen, wie diese Situation zu handhaben ist. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalog-Aktivität weiterleiten. Das Ereignis von Interesse ist das Ereignis zum Ändern des Status oder Status und der entsprechende Rückruf ist die Methode zum Ändern des on-Status. Der folgende Code überwacht, ob der Player seinen internen Status in FEHLER ändert:

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```
