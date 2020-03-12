---
description: Wenn pttrackingmode=simple oder ptplayer=ios-mobileweb, sendet der Manifestserver eine JSON-formatierte Datei zurück, die Master-M3U8 enthält, eine URL, über die der Client die M3U8-Datei mit einer Beschreibung des Inhalts anfordern kann.
seo-description: Wenn pttrackingmode=simple oder ptplayer=ios-mobileweb, sendet der Manifestserver eine JSON-formatierte Datei zurück, die Master-M3U8 enthält, eine URL, über die der Client die M3U8-Datei mit einer Beschreibung des Inhalts anfordern kann.
seo-title: JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste
title: JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste
uuid: 9f9693d0-3c93-4555-b20c-7f4576742f41
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# JSON-Format für URL zum Anfordern der varianten Manifestwiedergabeliste {#json-format-for-url-for-requesting-variant-manifest-playlist}

Wenn `pttrackingmode=simple` oder `ptplayer=ios-mobileweb`, sendet der Manifestserver eine JSON-formatierte Datei zurück, die Master-M3U8 enthält, eine URL, die der Client zum Anfordern der M3U8-Datei verwenden kann, die den Inhalt beschreibt.

Dies ist das Format der JSON-Datei, die die `Master-M3U8` URL enthält.

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
