---
description: Bei Live- und Video-On-Demand-Medien (VOD) beginnt TVSDK mit der Wiedergabe, indem es die Wiedergabeliste herunterlädt, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente herunterlädt. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.
title: Medienwiedergabe und Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Medienwiedergabe und Failover {#media-playback-and-failover}

Bei Live- und Video-On-Demand-Medien (VOD) beginnt TVSDK mit der Wiedergabe, indem es die Wiedergabeliste herunterlädt, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente herunterlädt. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.

## Fehlendes Wiedergabelisten-Failover {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

Wenn beispielsweise eine komplette Wiedergabeliste fehlt, versucht TVSDK, die in einer Manifestdatei der obersten Ebene angegebene Datei M3U8 nicht herunterzuladen. Wenn sie nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, fehlt, sucht TVSDK mit derselben Auflösung nach einer VariantenWiedergabeliste. Wenn es die gleiche Auflösung findet, lädt TVSDK die VariantenWiedergabeliste und die Segmente von der entsprechenden Position herunter. Wenn der Player nicht dieselbe Auflösungs-Wiedergabeliste findet, versucht er, andere Bitratenspiellisten und deren Varianten zu durchlaufen. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann ihre Variante usw. Wenn alle Wiedergabelisten mit niedrigerer Bitrate und ihre Varianten erschöpft sind, um eine gültige Wiedergabeliste zu finden, wird TVSDK zur höchsten Bitrate wechseln und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt in den ERROR-Status.

Ihre Anwendung kann bestimmen, wie diese Situation behandelt wird. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalogaktivität weiterleiten. Das Ereignis von Interesse ist die `STATUS_CHANGED` -Ereignis und der entsprechende Rückruf ist der `onStatusChanged` -Methode. Im Folgenden finden Sie Code, der überwacht, ob der Player seinen internen Status in `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Fehlendes Segment-Failover {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht TVSDK, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil z. B. die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw. versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen ausgeführt werden:

1. Versuchen Sie, in einer Variantendatei ein Failover für dasselbe Segment mit derselben Bitrate durchzuführen.
1. Wechseln Sie in derselben Datei zu einer alternativen Bitrate (ABR-Switch).
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung. Diese Benachrichtigung enthält eine innere Benachrichtigung mit der `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem ein alternativer Audio-Track ist, generiert TVSDK die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden kontinuierliche Segmentübergänge auf 5 begrenzt. Danach wird die Wiedergabe gestoppt und TVSDK gibt einen `NATIVE_ERROR` mit dem Code 5.

>[!NOTE]
>
>**Einschränkungen**
>
>Im Folgenden finden Sie einige Einschränkungen, die Sie kennen sollten:
>
>* Die ABR-Steuerungsparameter (Adaptive Bitrate) werden bei einem Failover nicht berücksichtigt.
>
>  Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass eine der derzeit verfügbaren Wiedergabelisten unabhängig von ihrem Bitratenprofil als Backup-Streams verwendet wird.
>* Während eines Failover-Vorgangs kann es einen Profilwechsel geben.
>
>  Wenn beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auftritt, werden ABR-Steuerungsparameter wie die erlaubte Min-/Max-Bitrate ignoriert.
