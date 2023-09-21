---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.
title: Wiedergabe und Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Wiedergabe und Failover {#playback-and-failover}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.

Primetime kann nicht vor solchen Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen. Primetime-Streaming bietet jedoch einen Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Server-Fehlern oder Betriebsausfällen zu schützen, wodurch das Erlebnis für Viewer verbessert wird. Browser TVSDK implementiert einen Failover-Schutz, um Unterbrechungen der Wiedergabe zu minimieren und trotz Übertragungsproblemen eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Medienset, wenn vollständige Ausgabedarstellungen oder Fragmente nicht verfügbar sind.

## Medienwiedergabe {#media-playback}

Bei Live- und VOD-Medien startet das Browser TVSDK die Wiedergabe, indem es die Wiedergabeliste herunterlädt, die mit der Bitrate der mittleren Auflösung verknüpft ist, und dann Segmente der Bitratenmedien mit mittlerer Auflösung herunterlädt, die von der Wiedergabeliste definiert werden.

Browser TVSDK wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.

## Fehlendes Wiedergabelisten-Failover {#section_81A5822C108449E1A0E94A6E25DE9E8E}

Wenn beispielsweise eine komplette Wiedergabeliste fehlt, wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht Browser TVSDK, die Wiedergabe wiederherzustellen. Wenn sie nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, fehlt, sucht Browser TVSDK mit derselben Auflösung nach einer VariantenWiedergabeliste. Wenn sie die gleiche Auflösung findet, beginnt sie mit dem Download der Varianten-Wiedergabeliste und der Segmente von der entsprechenden Position. Wenn Browser TVSDK nicht dieselbe Auflösungs-Playlist findet, wird versucht, andere Bitratenspiellisten und deren Varianten zu durchlaufen. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann ihre Variante usw. Wenn alle Wiedergabelisten mit niedrigerer Bitrate und ihre Varianten beim Versuch, eine gültige Wiedergabeliste zu finden, erschöpft sind, wird Browser TVSDK zur obersten Bitrate wechseln und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt in den ERROR-Status.

Ihre Anwendung kann bestimmen, wie diese Situation behandelt wird. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalogaktivität weiterleiten. Das Ereignis von Interesse ist das Ereignis, bei dem der Status oder der Status geändert wurde, und der entsprechende Rückruf ist die Methode bei Statusänderung . Im Folgenden finden Sie Code, der überwacht, ob der Player seinen internen Status in ERROR ändert:

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```
