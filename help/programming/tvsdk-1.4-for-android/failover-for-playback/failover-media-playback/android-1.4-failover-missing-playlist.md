---
description: Wenn beispielsweise eine komplette Wiedergabeliste fehlt, wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK, die Wiedergabe wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, bestimmt Ihre Anwendung den nächsten Schritt.
title: Fehlendes Wiedergabelisten-Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Fehlendes Wiedergabelisten-Failover{#missing-playlist-failover}

Wenn beispielsweise eine komplette Wiedergabeliste fehlt, wenn die in einer Manifestdatei der obersten Ebene angegebene M3U8-Datei nicht heruntergeladen wird, versucht TVSDK, die Wiedergabe wiederherzustellen. Wenn die Wiederherstellung nicht möglich ist, bestimmt Ihre Anwendung den nächsten Schritt.

Wenn die Wiedergabeliste, die mit der Bitrate der mittleren Auflösung verknüpft ist, fehlt, sucht TVSDK mit derselben Auflösung nach einer VariantenWiedergabeliste. Wenn sie die gleiche Auflösung findet, beginnt sie mit dem Download der Varianten-Wiedergabeliste und der Segmente von der entsprechenden Position. Wenn TVSDK nicht dieselbe Auflösungs-Playlist findet, wird versucht, andere Bitratenspiellisten und deren Varianten zu durchlaufen. Eine unmittelbar niedrigere Bitrate ist die erste Wahl, dann ihre Variante usw. Wenn alle Wiedergabelisten mit niedrigerer Bitrate und ihre Varianten erschöpft sind, um eine gültige Wiedergabeliste zu finden, wird TVSDK zur höchsten Bitrate wechseln und von dort unten zählen. Wenn keine gültige Wiedergabeliste gefunden werden kann, schlägt der Prozess fehl und der Player wechselt in den ERROR-Status.

Ihre Anwendung kann bestimmen, wie diese Situation behandelt wird. Sie können beispielsweise die Player-Aktivität schließen und den Benutzer zur Katalogaktivität weiterleiten. Das Ereignis von Interesse ist die `STATE_CHANGED` -Ereignis und der entsprechende Rückruf ist der `onStateChanged` -Methode. Im Folgenden finden Sie Code, der überwacht, ob der Player seinen internen Status in ERROR ändert:

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

Weitere Informationen finden Sie unter [!DNL PlayerFragment.java] -Datei in Ihrem SDK:

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
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
