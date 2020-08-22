---
description: Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn wiedergegeben, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.
seo-description: Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn wiedergegeben, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.
seo-title: Medienwiedergabe und Failover
title: Medienwiedergabe und Failover
uuid: e0072eeb-8ad1-436f-bf4a-fee6885a25bd
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---


# Medienwiedergabe und Failover {#media-playback-and-failover}

Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn wiedergegeben, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.

## Fehlendes Wiedergabelisten-Failover {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

Wenn beispielsweise die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK, eine Wiederherstellung vorzunehmen. Wenn der Vorgang nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate mit mittlerer Auflösung verknüpft ist, fehlt, sucht TVSDK nach einer Varianten-Playlist mit derselben Auflösung. Wenn dieselbe Auflösung gefunden wird, laden TVSDK-Beginn die Wiedergabeliste und die Segmente von der entsprechenden Position herunter. Wenn der Player nicht dieselbe Auflösungs-Playlist findet, versucht er, durch andere Bitrate-Playlisten und deren Varianten zu blättern. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann die Variante usw. Wenn alle Playlisten mit niedriger Bitrate und ihre Varianten erschöpft sind, um eine gültige Playlist zu finden, wird TVSDK zur obersten Bitrate gehen und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt zum FEHLER-Status.

Ihre Anwendung kann bestimmen, wie diese Situation zu handhaben ist. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalog-Aktivität weiterleiten. Das gewünschte Ereignis ist das `STATUS_CHANGED` Ereignis und der entsprechende Rückruf ist die `onStatusChanged` Methode. Der folgende Code überwacht, ob der Player seinen internen Status in `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Fehlendes Segmentfailover {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht TVSDK, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil beispielsweise die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw., versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen ausgeführt werden:

1. Versucht in einer Variantendatei ein Failover mit derselben Bitrate auf dasselbe Segment.
1. Wechseln Sie zu einer alternativen Bitrate (ABR Switch) in derselben Datei.
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung ausgelöst. Diese Benachrichtigung enthält eine innere Benachrichtigung mit dem `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem eine alternative Audiospur ist, generiert TVSDK die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden fortlaufende Segmentübergänge auf 5 begrenzt. Danach wird die Wiedergabe gestoppt und TVSDK gibt einen `NATIVE_ERROR` Code 5 aus.

>[!NOTE]
>
>**Einschränkungen**
>
>Im Folgenden finden Sie einige Einschränkungen, die Sie beachten sollten:
>
>* Die ABR-Steuerungsparameter (adaptive Bitrate) werden bei einem Failover nicht berücksichtigt.
>
>  
Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass eine der derzeit verfügbaren Playlisten unabhängig von ihrem Bitrate-Profil als Sicherungsströme verwendet wird.
>* Während eines Failover-Vorgangs kann es einen Profil-Switch geben.
>
>  
Tritt beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auf, werden ABR-Steuerungsparameter wie die zulässige Min-/Max-Bitrate ignoriert.
