---
description: Durch das parallele Herunterladen von Video und Audio statt in einer Serie werden Starterverzögerungen reduziert.
title: Parallele Downloads
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Parallele Downloads {#parallel-downloads}

Durch das parallele Herunterladen von Video und Audio statt in einer Serie werden Starterverzögerungen reduziert.

Parallel-Downloads ermöglichen die Wiedergabe von VOD-Dateien (Video-on-Demand), optimieren die verfügbare Bandbreitennutzung von einem Server, verringern die Wahrscheinlichkeit, in Pufferuntersituationen zu geraten, und minimieren die Verzögerung zwischen Download und Wiedergabe.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Ohne parallele Downloads stellt TVSDK eine Anforderung für das Videosegment aus. Nachdem das Videosegment geladen wurde, werden ein oder zwei Audiosegmente angefordert. Bei parallelen Downloads werden die Audio- und Videosegmente gleichzeitig heruntergeladen, nicht sequenziell. Da es parallel zwei Verbindungen und zwei HTTP-Anforderungen pro Segment gibt, erreichen die Daten schneller den Bildschirm.

>[!NOTE]
>
>Diese Funktion gilt nur für Inhalte, bei denen Audio und Video in verschiedene Dateien kodiert sind (unstummschalteter Inhalt), nicht aber für MP4-Inhalte, die immer maskiert werden. HLS-Inhalte sind oft unmuliert, insbesondere bei alternativen Audio-Aufnahmen.

<!-- 

See comment above (DASH use case removed).
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

Bei der HTTP-Verbindung kann es in den folgenden Phasen zu Verzögerungen kommen:

* Beim Herstellen der TCP/IP-Verbindung zum Server

  Obwohl der Client und der Server der Kommunikation zugestimmt haben, ist noch keine HTTP-Kommunikation aufgetreten. Diese Verzögerung hängt von der Infrastruktur zwischen Client und Server ab. Dieser Prozess erfordert die Suche eines Pfades durch das Internet zwischen Client und Server und die Sicherstellung, dass alle Geräte, wie Router und Firewalls, auf der Route der Datenübertragung zustimmen.
* Beim Senden einer HTTP-Anforderung für ein Segment oder ein Manifest über die TCP/IP-Verbindung.

  Der Server empfängt die Anforderung, verarbeitet sie und beginnt mit dem Zurücksenden der Daten an den Client. Die Verzögerung hängt von der Auslastung und der Komplexität der Software auf dem Server sowie in gewissem Maße von der Upload-Verbindungsgeschwindigkeit ab, wenn der Client die Anfrage sendet.
