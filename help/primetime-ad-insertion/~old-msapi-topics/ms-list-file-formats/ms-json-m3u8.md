---
description: Wenn pttrackingmode=simple oder ptplayer=ios-mobileweb, sendet der Manifestserver eine JSON-formatierte Datei zurück, die Übergeordnet-M3U8 enthält, eine URL, über die der Client die M3U8-Datei mit einer Beschreibung des Inhalts anfordern kann.
seo-description: Wenn pttrackingmode=simple oder ptplayer=ios-mobileweb, sendet der Manifestserver eine JSON-formatierte Datei zurück, die Übergeordnet-M3U8 enthält, eine URL, über die der Client die M3U8-Datei mit einer Beschreibung des Inhalts anfordern kann.
seo-title: JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste
title: JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste
uuid: 9f9693d0-3c93-4555-b20c-7f4576742f41
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# JSON-Format für URL zum Anfordern der varianten Manifest-Wiedergabeliste {#json-format-for-url-for-requesting-variant-manifest-playlist}

Wenn `pttrackingmode=simple` oder `ptplayer=ios-mobileweb` der Manifestserver eine JSON-formatierte Datei zurücksendet, die Übergeordnet-M3U8 enthält, eine URL, über die der Client die M3U8-Datei mit einer Beschreibung des Inhalts anfordern kann.

Dies ist das Format der JSON-Datei mit der URL `Master-M3U8`.

```
{
"Master-M3U8": "https://manifest.auditude.com/auditude/variant/{publisherAssetID}/
  {sessionId}/{Base 64 of the url of the content}.m3u8
  ?u={Ad Request Id}
  &z={Ad Zone Id}
  &pttrackingmode=simple
  &pttrackingversion=v1
  &{other query parameters}"
}
```
