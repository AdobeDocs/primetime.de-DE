---
description: Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn abgespielt, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate in mittlerer Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.
seo-description: Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn abgespielt, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate in mittlerer Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.
seo-title: Medienwiedergabe und Failover
title: Medienwiedergabe und Failover
uuid: 197a6ee0-f1ff-40ac-bd49-eafeae6167d4
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Medienwiedergabe und Failover{#media-playback-and-failover}

Bei Live- und Video-on-Demand-Medien (VOD) werden TVSDK-Beginn abgespielt, indem die Wiedergabeliste heruntergeladen wird, die mit der Bitrate in mittlerer Auflösung verknüpft ist, und die von dieser Wiedergabeliste definierten Mediensegmente heruntergeladen werden. Sie wählt schnell die Wiedergabeliste mit hoher Bitrate und die zugehörigen Medien aus und fährt mit dem Herunterladen fort.

## Fehlendes Wiedergabelisten-Failover {#section_E6B6A15930894F56A0A8501577B35E7F}

Wenn eine vollständige Wiedergabeliste fehlt, z. B. wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK eine Wiederherstellung. Wenn der Vorgang nicht wiederhergestellt werden kann, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate mit mittlerer Auflösung verknüpft ist, fehlt, sucht TVSDK nach einer Varianten-Playlist mit derselben Auflösung. Wenn die gleiche Auflösung gefunden wird, werden die Variantenplaylist und die Segmente von der entsprechenden Position heruntergeladen. Wenn TVSDK nicht die gleiche Auflösungs-Playlist findet, wird versucht, durch andere Bitrate-Playlists und deren Varianten zu blättern. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann die Variante usw. Wenn alle Playlisten mit niedriger Bitrate und ihre Varianten erschöpft sind, um eine gültige Playlist zu finden, wird TVSDK zur obersten Bitrate gehen und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt zum FEHLER-Status.

Ihre Anwendung kann bestimmen, wie diese Situation zu handhaben ist. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalog-Aktivität weiterleiten. Das gewünschte Ereignis ist das `STATUS_CHANGED` Ereignis und der entsprechende Rückruf ist die `onStatusChange` Methode. Der folgende Code überwacht, ob der Player seinen internen Status in FEHLER ändert:

Weitere Informationen finden Sie in der `PSDKDemo` Datei. Ereignis-Listener werden an die MediaPlayer-Instanz angehängt.

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

Die API stellt die URL bereit, mit der überprüft wird, ob das clientseitige Netzwerk ausfällt. Dies sollte eine gültige URL sein, die HTTP-Antwortcode 200 bei HTTP-Anforderungen zurückgibt.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Wenn setNetworkDownVerificationUrl nicht eingestellt ist, verwendet TVSDK standardmäßig die MainManifest-URL, um festzustellen, ob das Netzwerk ausfällt.

## Fehlendes Segmentfailover {#section_ED8CF666289042D39E9914D42BDD9BA4}

Wenn ein Segment fehlt, z. B. wenn ein bestimmtes Segment nicht heruntergeladen werden kann, versucht TVSDK, sich über eine Vielzahl von Failover-Versuchen wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, wird ein Fehler ausgegeben.

Wenn ein Segment auf dem Server fehlt, weil beispielsweise die Manifestdatei nicht vorhanden ist, das Segment nicht heruntergeladen werden kann usw., versucht TVSDK, einen Fehler zu beheben, indem folgende Optionen ausgeführt werden:

1. Versucht in einer Variantendatei ein Failover mit derselben Bitrate auf dasselbe Segment.
1. Wechseln Sie zu einer alternativen Bitrate (ABR Switch) in derselben Datei.
1. Durchlaufen Sie jede verfügbare Bitrate in jeder verfügbaren Variante.
1. Überspringen Sie das Segment und geben Sie eine Warnung aus.

Wenn TVSDK kein alternatives Segment abrufen kann, wird eine `CONTENT_ERROR` Fehlerbenachrichtigung ausgelöst. Diese Benachrichtigung enthält eine innere Benachrichtigung mit dem Code- `DOWNLOAD_ERROR` Code. Wenn der Stream mit dem Problem eine alternative Audiospur ist, generiert TVSDK die `AUDIO_TRACK_ERROR` Fehlerbenachrichtigung.

Wenn die Video-Engine kontinuierlich keine Segmente abrufen kann, werden fortlaufende Segmentübergänge auf 5 begrenzt. Danach wird die Wiedergabe gestoppt und TVSDK gibt einen `NATIVE_ERROR` Code 5 aus.

>[!NOTE]
>
>Die ABR-Steuerungsparameter (adaptive Bitrate) werden bei einem Failover nicht berücksichtigt. Der Grund dafür ist, dass der Failover-Mechanismus so konzipiert ist, dass alle derzeit verfügbaren Wiedergabelisten unabhängig von ihrem Bitrate-Profil als Backup-Streams verwendet werden können.
>
>Während eines Failover-Vorgangs kann es einen Profil-Switch geben. Tritt beim Herunterladen eines der Wiedergabelistensegmente ein Fehler auf, werden ABR-Steuerungsparameter wie die zulässige Min-/Max-Bitrate ignoriert.

