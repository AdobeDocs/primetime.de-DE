---
description: Bei Live- und Video-On-Demand-Medien (VOD) beginnt TVSDK mit der Wiedergabe, indem es die Wiedergabeliste herunterlädt, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente herunterlädt. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.
title: Medienwiedergabe und Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---

# Medienwiedergabe und Failover{#media-playback-and-failover}

Bei Live- und Video-On-Demand-Medien (VOD) beginnt TVSDK mit der Wiedergabe, indem es die Wiedergabeliste herunterlädt, die mit der Bitrate der mittleren Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente herunterlädt. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und setzt den Download fort.

## Fehlendes Wiedergabelisten-Failover {#section_E6B6A15930894F56A0A8501577B35E7F}

Wenn beispielsweise eine komplette Wiedergabeliste fehlt, wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK, die Wiedergabe wiederherzustellen. Wenn sie nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, fehlt, sucht TVSDK mit derselben Auflösung nach einer VariantenWiedergabeliste. Wenn sie die gleiche Auflösung findet, beginnt sie mit dem Download der Varianten-Wiedergabeliste und der Segmente von der entsprechenden Position. Wenn TVSDK nicht dieselbe Auflösungs-Playlist findet, wird versucht, andere Bitratenspiellisten und deren Varianten zu durchlaufen. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann ihre Variante usw. Wenn alle Wiedergabelisten mit niedrigerer Bitrate und ihre Varianten erschöpft sind, um eine gültige Wiedergabeliste zu finden, wird TVSDK zur höchsten Bitrate wechseln und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt in den ERROR-Status.

Ihre Anwendung kann bestimmen, wie diese Situation behandelt wird. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalogaktivität weiterleiten. Das Ereignis von Interesse ist die `STATUS_CHANGED` -Ereignis und der entsprechende Rückruf ist der `onStatusChange` -Methode. Im Folgenden finden Sie Code, der überwacht, ob der Player seinen internen Status in ERROR ändert:

Weitere Informationen finden Sie unter `PSDKDemo` -Datei. Ereignis-Listener werden an die MediaPlayer-Instanz angehängt.

```
case MediaPlayerStatus.ERROR: 
Alert.show(event.error.toString(), “Error occurred”); 
break;
```

Wenn das clientseitige Netzwerk ausfällt, können Sie diesen Code zur Überprüfung verwenden.

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

Die API stellt die URL bereit, mit der überprüft wird, ob das clientseitige Netzwerk ausfällt. Dies sollte eine gültige URL sein, die HTTP-Antwort-Code 200 für HTTP-Anfragen zurückgibt.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Wenn setNetworkDownVerificationUrl nicht festgelegt ist, verwendet TVSDK standardmäßig die MainManifest-URL, um zu ermitteln, ob das Netzwerk ausfällt.

## Fehlendes Segment-Failover {#section_ED8CF666289042D39E9914D42BDD9BA4}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht TVSDK, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil z. B. die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw. versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen verwendet werden:

1. Versuchen Sie, in einer Variantendatei ein Failover für dasselbe Segment mit derselben Bitrate durchzuführen.
1. Wechseln Sie in derselben Datei zu einer alternativen Bitrate (ABR-Switch).
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung. Diese Benachrichtigung enthält eine innere Benachrichtigung mit dem Code `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem ein alternativer Audio-Track ist, generiert TVSDK die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden kontinuierliche Segmentübergänge auf 5 begrenzt. Danach wird die Wiedergabe gestoppt und TVSDK gibt einen `NATIVE_ERROR` mit dem Code 5.

>[!NOTE]
>
>Die ABR-Steuerungsparameter (Adaptive Bitrate) werden bei einem Failover nicht berücksichtigt. Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass eine der derzeit verfügbaren Wiedergabelisten unabhängig von ihrem Bitratenprofil als Backup-Streams verwendet wird.
>
>Während eines Failover-Vorgangs kann es einen Profilwechsel geben. Wenn beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auftritt, werden ABR-Steuerungsparameter wie die erlaubte Min-/Max-Bitrate ignoriert.
