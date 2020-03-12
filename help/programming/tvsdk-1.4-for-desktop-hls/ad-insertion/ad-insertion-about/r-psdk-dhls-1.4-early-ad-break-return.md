---
description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-description: Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
seo-title: Implementieren der Rückgabe einer frühen Werbeunterbrechung
title: Implementieren der Rückgabe einer frühen Werbeunterbrechung
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Implementieren der Rückgabe einer frühen Werbeunterbrechung{#implementing-an-early-ad-break-return}

Beim Einfügen von Livestream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

>[!NOTE] {othertype=&quot;Prerequisite&quot;}
>
>Sie müssen die Abmeldung-/In-Anzeigenmarken ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`und `#EXT-X-CUE`) abonnieren.

Es gibt einige zu berücksichtigende Anforderungen:

* Parsen Sie Markierungen wie `EXT-X-CUE-IN` (oder ein äquivalentes Marker-Tag), die in den linearen oder FER-Streams angezeigt werden.

   Registrieren Sie die Markierungen als Marker für den Anzeigenrückkehrpunkt. Wird nur `adBreaks` bis zu dieser Markerposition während der Wiedergabe abgespielt, wodurch die Dauer der `adBreak` durch die führende `EXE-X-CUE-OUT` Markierung markierten Markierung überschrieben wird.

* Wenn zwei `EXT-X-CUE-IN` Markierungen für dieselbe `EXT-X-CUE-OUT` Markierung vorhanden sind, wird als erste `EXT-X-CUE-IN` Markierung die gezählte Markierung angezeigt.

* Wenn die `EXE-X-CUE-IN` Markierung in der Zeitleiste ohne führende `EXT-X-CUE-OUT` Markierung angezeigt wird, wird die `EXE-X-CUE-IN` Markierung verworfen.

   Wenn der führende `EXT-X-CUE-OUT` Marker in einem Live-Stream gerade aus dem Fenster gezogen ist, reagiert das TVSDK nicht darauf.

* Wenn eine Werbeunterbrechung frühzeitig zurückgegeben wird, wird `adBreak` abgespielt, bis die Abspielleiste an die ursprüngliche Position zurückkehrt, an der die Werbeunterbrechung beendet werden sollte, und die Wiedergabe des Hauptinhalts von dieser Position an fortgesetzt.

## SpliceOut und SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` und `SpliceIn` Markierungen markieren den Anfang und das Ende der Werbeunterbrechung. Die Dauer des `SpliceOut` Markentyps `EXE-X-CUE` kann null betragen, und der `SpliceIn` Typ der `EXE-X-CUE` Markierung markiert das Ende der Werbeunterbrechung. Sie werden in einem Tag angezeigt und unterscheiden sich nach Typ.

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

Wenn die Dauer des `SpliceOut` Typs bei einer Marke mit verschiedenen Typen null ist, muss bei jeder Werbeunterbrechung der Wert `SpliceOut` und `SpliceIn` zusammenarbeiten. Derzeit ist eine `SpliceOut` Markierung mit einer Dauer von nicht null und ohne `SpliceIn` Pairing-Markierungen typischer.

**Zwei separate Markierungen**

Das typischere Szenario ist ein `SpliceOut` Marker mit einer Dauer von ungleich null, der keine `SpliceIn` Paarungsmarkierungen benötigt. Hier markiert eine `SpliceIn` Paarungsmarke das Ende der Werbeunterbrechung während der Wiedergabe der Werbeunterbrechung, aber die Werbeunterbrechung wird an der `SpliceIn` Markerposition abgeschnitten und die Hauptinhaltsunterbrechung wird an dieser Position wiedergegeben.

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

