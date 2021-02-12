---
description: Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.
seo-description: Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.
seo-title: VOD-Timeline ersetzen
title: VOD-Timeline ersetzen
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# VOD-Zeitleiste {#replace-a-vod-timeline} ersetzen

Ersetzen Sie eine VOD-Zeitleiste, indem Sie eine neue Anzeigeneinfügeanforderung an den Manifestserver mit einem entsprechend festgelegten Parameter für die Abfrage der pttimeline senden.

1. Bereiten Sie eine Anzeigeneinfügungsanforderung wie gewohnt vor.
1. Setzen Sie den Parameter `ptcueformat` Abfrage auf DPIScte35.
1. Legen Sie für den Parameter `enableC3` der Abfrage den Wert true oder false fest.
1. Erstellen Sie einen Parameter `pttimeline` mithilfe des VOD-Zeitschienenformats:
   1. Geben Sie jeden Inhaltsblock (Kapitel) mit `duration = 0` und `number_of_lots = 1` an.
   1. Geben Sie jeden Anzeigenblock wie gewohnt an, stellen Sie jedoch `lots = 0` ein, um einen Umbruch zu entfernen. Legen Sie `duration = 0` fest, um die Dauer der Werbeunterbrechung zu verwenden (aus der Datei M3U8).

## Beispiel: Ersetzen einer VOD-Timeline

In diesem Beispiel wird davon ausgegangen, dass sich der VOD-Inhalt in `Original.m3u8` mit einer Zeitleiste von `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;` befindet

Die folgende Manifestserveranforderung ersetzt die Umbrüche in `Original.m3u8` durch eine 30-sekündige Pre-Roll-Unterbrechung, gefolgt von zwei Unterbrechungen von jeweils zwei Minuten.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

Die folgende Manifestserveranforderung entfernt die Umbrüche in `Original.m3u8` und fügt eine 30-Sekunden-Pre-Roll- und eine 30-Sekunden-Post-Roll hinzu.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
