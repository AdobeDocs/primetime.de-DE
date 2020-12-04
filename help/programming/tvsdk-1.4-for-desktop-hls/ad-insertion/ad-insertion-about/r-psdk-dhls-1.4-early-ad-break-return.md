---
description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-title: Implementieren der Rückgabe einer frühen Werbeunterbrechung
title: Implementieren der Rückgabe einer frühen Werbeunterbrechung
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# Implementieren einer Zeilenumbruch-Frühanzeige{#implementing-an-early-ad-break-return}

Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

>[!NOTE]
>
>Sie müssen die Splice-out-/In-Anzeigenmarken ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN` und `#EXT-X-CUE`) abonnieren.

Es gibt einige zu berücksichtigende Anforderungen:

* Parsen Sie Markierungen wie `EXT-X-CUE-IN` (oder ein äquivalentes Marker-Tag), die in den linearen oder FER-Streams angezeigt werden.

   Registrieren Sie die Markierungen als Marker für den Anzeigenrückkehrpunkt. Wiedergabe von `adBreaks` nur bis zu dieser Markenposition während der Wiedergabe, wodurch die Dauer von `adBreak`, die durch die führende `EXE-X-CUE-OUT`-Markierung gekennzeichnet ist, außer Kraft gesetzt wird.

* Wenn zwei `EXT-X-CUE-IN`-Markierungen für dieselbe `EXT-X-CUE-OUT`-Markierung vorhanden sind, wird die erste `EXT-X-CUE-IN`-Markierung angezeigt, die zählt.

* Wenn die `EXE-X-CUE-IN`-Markierung in der Zeitleiste ohne führende `EXT-X-CUE-OUT`-Markierung angezeigt wird, wird die `EXE-X-CUE-IN`-Markierung verworfen.

   Wenn in einem Live-Stream die führende `EXT-X-CUE-OUT`-Markierung gerade aus dem Fenster verschoben wurde, reagiert das TVSDK nicht darauf.

* Bei einer frühen Rückkehr aus einer Werbeunterbrechung wird das `adBreak` so lange abgespielt, bis die Abspielleiste an die ursprüngliche Position zurückkehrt, an der die Werbeunterbrechung beendet werden sollte, und die Wiedergabe des Hauptinhalts von dieser Position an fortgesetzt.

## SpliceOut und SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` und  `SpliceIn` Markierungen markieren den Anfang und das Ende der Werbeunterbrechung. Die Dauer des `SpliceOut`-Typs der `EXE-X-CUE`-Markierung kann null sein, und der `SpliceIn`-Typ der `EXE-X-CUE`-Markierung markiert das Ende der Werbeunterbrechung. Sie werden in einem Tag angezeigt und unterscheiden sich nach Typ.

**Eine Marke mit verschiedenen Typen**

Beispiel: Es gibt hier einen Marker mit verschiedenen Typen:

```
#EXTM3U#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:3
#EXT-X-MEDIA-SEQUENCE:44
  
#EXTINF:9.9,
https://server-host/path/file44.ts
#EXTINF:4.2,
https://server-host/path/file45.ts
  
#EXT-X-CUE:TYPE="SpliceOut",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138",AVAIL-NUM="1",AVAILS-EXPECTED="10"
#EXTINF:5.8,
https://server-host/path/file46.ts
#EXTINF:9.9,
https://server-host/path/file47.ts
...
#EXTINF:9.9,
https://server-host/path/file56.ts
#EXTINF:4.2,
https://server-host/path/file57.ts
#EXT-X-CUE:TYPE="SpliceIn",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138"
#EXTINF:9.9,
https://server-host/path/file58.ts
```

Wenn die Dauer des Typs `SpliceOut` bei einer Marke mit verschiedenen Typen null ist, müssen `SpliceOut` und `SpliceIn` bei jeder Werbeunterbrechung zusammenarbeiten. Derzeit ist eine `SpliceOut`-Markierung mit einer Dauer von ungleich null und benötigt keine Paarung von `SpliceIn`-Markern.

**Zwei separate Markierungen**

Das typischere Szenario ist ein `SpliceOut`-Marker mit einer Dauer von ungleich null, der keine Paarung `SpliceIn`-Markierungen benötigt. Hier markiert eine Paarung mit der Markierung `SpliceIn` das Ende der Werbeunterbrechung während der Wiedergabe der Werbeunterbrechung, aber der Werbeunterbrechung wird an der `SpliceIn`-Markenposition abgeschnitten und die Beginn mit dem Hauptinhalt an dieser Position.

Hier sind beispielsweise zwei verschiedene Marker:

```
#EXT-X-CUE-OUT:ID=105,DURATION=30.0,TIME=1081.08
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589090425811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589150485811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589210545811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589270605811,format=m3u8-aapl-v4)
#EXT-X-CUE-IN:ID=105,TIME=1105.104
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589330665811,format=m3u8-aapl-v4)
```

