---
description: Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.
title: Mehrere Bitratenströme
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Mehrere Bitratenströme {#multiple-bit-rate-streams}

Client-Anforderungen zum Einfügen von Anzeigen geben in der Wiedergabeliste im M3U8-Format normalerweise mehr als eine Bitrate an. Der Manifestserver erzeugt und gibt eine neue Variante der M3U8-Datei zurück, die einen separaten M3U8-Link für jede Bitrate enthält. Es wird auch eine eindeutige Gruppen-ID generiert, um diese M3U8s miteinander zu verbinden.

Der Manifestserver verwendet die Informationen in der URL-Anforderung des Bootstrap des Clients, um die Wiedergabeliste für Inhaltsvarianten abzurufen. Es wird eine neue variante Wiedergabeliste mit Manifestserverlinks zu Stream-Inhalten generiert. Der Client verwendet diese zum Erstellen von Anzeigeneinfügeanforderungen. Die Inhaltsverknüpfungen auf Stream-Ebene des Manifestservers haben das folgende Format:

```
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
  {groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **`live/vod`** Der Manifestserver legt diesen Wert basierend auf dem Wiedergabelististyp des Inhalts fest: Live/linear (#EXT-X-PLAYLIST-TYPE:EREIGNIS) oder VOD (#EXT-X-PLAYLIST-TYPE:VOD)

* **`publisherAssetID`** Die eindeutige ID des Herausgebers für den spezifischen Inhalt, der in der URL-Anforderung des Bootstrap bereitgestellt wird.

* **`rendition`** Der Manifestserver legt dies auf Grundlage des BANDWIDTH-Werts des Inhaltsstreams fest und verwendet ihn, um die Bitrate der Anzeige mit der Bitrate des Inhalts abzugleichen. Die Bitrate der Anzeige darf die Bitrate des Inhalts nur überschreiten, wenn die Anzeigenwiedergabe mit der niedrigsten Bitrate dies tut.

* **`groupID`** Der Manifestserver erzeugt diesen Wert und stellt damit sicher, dass er Anzeigen konsistent platziert, unabhängig davon, für welche Bitratendarstellungen der Client Anzeigen anfordert.

* **`base64-encoded url of the bit rate stream`** Die URL-sichere Basis des Manifestservers 64 kodiert die absolute URL des Inhaltsstreams. Jeder Stream hat seine eigene URL.

* **`Query parameters`** In der Bootstrap-URL-Anforderung bereitgestellte Abfragen.

