---
description: Wenn eine vollständige Wiedergabeliste fehlt, z. B. wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK eine Wiederherstellung. Wenn die Wiederherstellung nicht möglich ist, bestimmt Ihre Anwendung den nächsten Schritt.
title: Fehlendes Wiedergabelisten-Failover
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Fehlendes Playlist-Failover{#missing-playlist-failover}

Wenn eine vollständige Wiedergabeliste fehlt, z. B. wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK eine Wiederherstellung. Wenn die Wiederherstellung nicht möglich ist, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate mit mittlerer Auflösung verknüpft ist, fehlt, sucht TVSDK nach einer Varianten-Playlist mit derselben Auflösung. Wenn die gleiche Auflösung gefunden wird, werden die Variantenplaylist und die Segmente von der entsprechenden Position heruntergeladen. Wenn TVSDK nicht die gleiche Auflösungs-Playlist findet, wird versucht, durch andere Bitrate-Playlists und deren Varianten zu blättern. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann die Variante usw. Wenn alle Playlisten mit niedrigeren Bitraten und ihre Varianten erschöpft sind, um eine gültige Playlist zu finden, wird TVSDK zur obersten Bitrate gehen und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt zum FEHLER-Status.

Ihre Anwendung kann bestimmen, wie diese Situation zu handhaben ist. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalog-Aktivität weiterleiten. Das gewünschte Ereignis ist das Ereignis `STATE_CHANGED` und der entsprechende Rückruf ist die `onStateChanged`-Methode. Der folgende Code überwacht, ob der Player seinen internen Status in FEHLER ändert:

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

Weitere Informationen finden Sie in der Datei [!DNL PlayerFragment.java] in Ihrem SDK:

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
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
