---
description: Durch das parallele Herunterladen von Video und Audio statt in einer Reihe werden Verzögerungen beim Start verringert.
seo-description: Durch das parallele Herunterladen von Video und Audio statt in einer Reihe werden Verzögerungen beim Start verringert.
seo-title: Parallele Downloads
title: Parallele Downloads
uuid: fa3edb50-7c24-433c-bc50-72d6cf73d834
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Parallele Downloads {#parallel-downloads}

Durch das parallele Herunterladen von Video und Audio statt in einer Reihe werden Verzögerungen beim Start verringert.

Parallel-Downloads ermöglichen die Wiedergabe von VOD-Dateien (Video-on-Demand), optimieren die verfügbare Bandbreitennutzung von einem Server, verringern die Wahrscheinlichkeit, in Puffersituationen zu gelangen, und minimieren die Verzögerung zwischen Download und Wiedergabe.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Ohne parallele Downloads stellt TVSDK eine Anforderung für das Videosegment aus. Nach dem Laden des Videosegments werden ein oder zwei Audiosegmente angefordert. Bei parallelen Downloads werden die Audio- und Videosegmente gleichzeitig heruntergeladen, nicht sequenziell. Da parallel zwei Verbindungen und zwei HTTP-Anforderungen vorhanden sind, erreichen die Daten schneller den Bildschirm.

>[!NOTE]
>
>Diese Funktion gilt nur für Inhalte, bei denen Audio und Video in verschiedenen Dateien kodiert werden (nicht-stummgeschaltet), nicht für MP4-Inhalte, die immer gemustert werden. HLS-Inhalte werden oft unkomprimiert, insbesondere bei alternativen Audiodaten.

<!-- 

See comment above (DASH use case removed).
<note type="restriction">
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
</note>

 -->

Die HTTP-Verbindung kann in den folgenden Phasen zu Verzögerungen führen:

* Beim Herstellen der TCP/IP-Verbindung zum Server

   Obwohl Client und Server sich zur Kommunikation bereit erklärt haben, ist noch keine HTTP-Kommunikation aufgetreten. Diese Verzögerung hängt von der Infrastruktur zwischen Client und Server ab. Dieser Prozess erfordert die Suche nach einem Pfad durch das Internet zwischen Client und Server und sicherzustellen, dass alle Geräte, wie Router und Firewalls, auf der Route der Datenübertragung zustimmen.
* Beim Senden einer HTTP-Anforderung für ein Segment oder ein Manifest über die TCP/IP-Verbindung.

   Der Server empfängt die Anforderung, verarbeitet sie und Beginn senden die Daten zurück an den Client. Der Grad der Verzögerung hängt von der Belastung und der Komplexität der Software auf dem Server und in gewissem Maße von der Upload-Verbindungsgeschwindigkeit ab, wenn der Client die Anforderung sendet.

