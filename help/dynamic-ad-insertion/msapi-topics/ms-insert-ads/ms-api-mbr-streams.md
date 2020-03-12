---
description: Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.
seo-description: Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.
seo-title: Mehrere Bitratenströme
title: Mehrere Bitratenströme
uuid: f59cb765-e000-43e0-8d3a-8149a3c5b96e
translation-type: tm+mt
source-git-commit: 2c7ac5c1b2d30b7eb819157ee4568739c1bdfb9d

---


# Mehrere Bitratenströme {#multiple-bit-rate-streams}

Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.

Der Manifestserver nutzt die Informationen in der Bootstrap-URL-Anforderung des Clients, um die Inhaltsvarianten-Wiedergabeliste abzurufen. Es wird eine neue variante Wiedergabeliste mit Manifestserverlinks zu Stream-Inhalten generiert. Der Client verwendet diese zum Erstellen von Anzeigeneinfügeanforderungen. Die Inhaltsverknüpfungen auf Stream-Ebene des Manifestservers haben das folgende Format:

```
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
  {groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **`live/vod`** Der Manifestserver legt diesen Wert basierend auf dem Wiedergabelististyp des Inhalts fest: Live/linear (#EXT-X-PLAYLIST-TYPE:EREIGNIS) oder VOD (#EXT-X-PLAYLIST-TYPE:VOD)

* **`publisherAssetID`** Die eindeutige ID des Herausgebers für den spezifischen Inhalt, der in der Bootstrap-URL-Anforderung bereitgestellt wird.

* **`rendition`** Der Manifestserver legt dies auf Grundlage des BANDWIDTH-Werts des Inhaltsstreams fest und verwendet ihn, um die Bitrate der Anzeige mit der Bitrate des Inhalts abzugleichen. Die Bitrate der Anzeige darf die Bitrate des Inhalts nur überschreiten, wenn die Anzeigenwiedergabe mit der niedrigsten Bitrate dies tut.

* **`groupID`** Der Manifestserver erzeugt diesen Wert und stellt damit sicher, dass er Anzeigen konsistent platziert, unabhängig davon, für welche Bitratendarstellungen der Client Anzeigen anfordert.

* **`base64-encoded url of the bit rate stream`** Die URL-sichere Basis des Manifestservers 64 kodiert die absolute URL des Inhaltsstreams. Jeder Stream hat seine eigene URL.

* **`Query parameters`** In der Bootstrap-URL-Anforderung bereitgestellte Abfragen.

