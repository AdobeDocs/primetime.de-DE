---
description: Für das Einfügen von Live-Stream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.
title: Implementieren einer frühen Werbeunterbrechung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Implementieren einer frühen Werbeunterbrechung{#implementing-an-early-ad-break-return}

Für das Einfügen von Live-Stream-Anzeigen müssen Sie möglicherweise eine Werbeunterbrechung beenden, bevor alle Anzeigen in der Werbeunterbrechung bis zum Ende wiedergegeben werden.

>[!NOTE]
>
>Sie müssen die Aufteilung/Verwendung der Anzeigenmarkierungen ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, und `#EXT-X-CUE`).

Beachten Sie Folgendes:

* Analysieren Sie Markierungen wie `EXT-X-CUE-IN` (oder äquivalentes Marker-Tag), die in den linearen oder FER-Streams angezeigt werden.

  Registrieren Sie die Marker als Marker für den Anzeigenfrühen Rückkehrpunkt. Nur Wiedergabe `adBreaks` bis zu dieser Markerposition während der Wiedergabe, die die Dauer der `adBreak` durch einen vorangestellten `EXE-X-CUE-OUT` Markieren.

* Wenn zwei `EXT-X-CUE-IN` -Markierungen sind für dieselbe `EXT-X-CUE-OUT` Markierung, die erste `EXT-X-CUE-IN` Die angezeigte Markierung zählt.

* Wenn die Variable `EXE-X-CUE-IN` -Markierung wird in der Timeline ohne vorangestellten `EXT-X-CUE-OUT` Marker, `EXE-X-CUE-IN` -Markierung wird verworfen.

  In einem Live-Stream, wenn der führende `EXT-X-CUE-OUT` -Markierung gerade aus dem Fenster verschoben wurde, reagiert das TVSDK nicht darauf.

* Wenn es eine frühe Rückkehr aus einer Werbeunterbrechung gibt, wird die `adBreak` wird wiedergegeben, bis die Abspielleiste an die ursprüngliche Position zurückkehrt, an der die Werbeunterbrechung beendet werden sollte, und die Wiedergabe des Hauptinhalts von dieser Position an fortgesetzt wird.

## SpliceOut und SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` und `SpliceIn` Markierungen markieren den Anfang und das Ende der Werbeunterbrechung. Die Dauer der `SpliceOut` Typ der `EXE-X-CUE` -Markierung kann null sein und `SpliceIn` Typ von `EXE-X-CUE` -Markierung markiert das Ende der Werbeunterbrechung. Sie werden in einem Tag angezeigt und unterscheiden sich je nach Typ.

**Eine Markierung mit unterschiedlichen Typen**

Hier ist beispielsweise eine Markierung mit verschiedenen Typen:

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

Wenn die Dauer der `SpliceOut` type ist null, die `SpliceOut` und `SpliceIn` muss für jede Werbeunterbrechung zusammenarbeiten. Derzeit ist ein `SpliceOut` -Markierung mit einer Dauer ungleich null und erfordert keine Paarung `SpliceIn` -Markierungen sind typischer.

**Zwei separate Markierungen**

Das typischere Szenario ist ein `SpliceOut` -Markierung mit einer Dauer ungleich null , die keine Paarung benötigt `SpliceIn` Markierungen. Hier eine Paarung `SpliceIn` -Markierung markiert das Ende der Werbeunterbrechung während der Wiedergabe der Werbeunterbrechung, aber die Werbeunterbrechung wird am `SpliceIn` Markierungsposition und der Hauptinhalt beginnt an dieser Position.

Hier sind beispielsweise zwei separate Markierungen:

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
