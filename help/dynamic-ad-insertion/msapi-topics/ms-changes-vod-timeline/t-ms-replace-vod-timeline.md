---
description: Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.
seo-description: Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.
seo-title: VOD-Timeline ersetzen
title: VOD-Timeline ersetzen
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# VOD-Timeline ersetzen {#replace-a-vod-timeline}

Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.

1. Bereiten Sie eine Anzeigeneinfügungsanforderung wie gewohnt vor.
1. Legen Sie den Parameter `ptcueformat` Abfrage auf DPIScte35 fest.
1. Legen Sie für den Parameter `enableC3` &quot;Abfrage&quot;je nach Bedarf true oder false fest.
1. Erstellen Sie einen `pttimeline` Parameter im VOD-Timeline-Format:
   1. Geben Sie jeden Inhaltsblock (Kapitel) mit `duration = 0` und `number_of_lots = 1`an.
   1. Geben Sie jeden Anzeigenblock wie gewohnt an, aber legen Sie ihn `lots = 0` fest, um einen Umbruch zu entfernen. Legen Sie `duration = 0` die Dauer der Werbeunterbrechung fest (aus der Datei M3U8).

## Beispiel: Ersetzen einer VOD-Timeline

In diesem Beispiel wird davon ausgegangen, dass der VOD-Inhalt `Original.m3u8` mit einer Zeitleiste von `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

Die folgende Manifestserveranforderung ersetzt die Pausen in `Original.m3u8` einer 30-Sekunden-Pre-Roll-Unterbrechung, gefolgt von zwei Pausen von jeweils zwei Minuten Dauer.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

Die folgende Manifestserveranforderung entfernt die Pausen in `Original.m3u8` und fügt eine 30-Sekunden-Pre-Roll- und eine 30-Sekunden-Post-Roll hinzu.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
