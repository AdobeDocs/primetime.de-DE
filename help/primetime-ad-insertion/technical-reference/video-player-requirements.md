---
description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver angewiesen ist, um Anzeigen einzufügen und das Anzeigen-Tracking zu aktivieren.
title: Anforderungen an Videoplayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Anforderungen an Videoplayer {#video-player-requirements}

Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver angewiesen ist, um Anzeigen einzufügen und das Anzeigen-Tracking zu aktivieren.

Um die Primetime-Anzeigen-Einfüge-API verwenden zu können, muss ein Videoplayer Folgendes erfüllen:

* Kann die Position der Abspielleiste verfolgen, während der Inhalt wiedergegeben wird.
* Kann Tracking-URLs zum angegebenen Zeitpunkt anfordern.
* Wird auf einer Geräteplattform ausgeführt, die HLS v3 oder höher unterstützt, einschließlich:

   * PTS-Unterbrechungen, gekennzeichnet durch `EXT-X-DISCONTINUITY` tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Führt auf einer Plattform aus, die HTTP-Umleitungen und das Parsen von JSON unterstützt.
* Webbasierte Player müssen auf Plattformen ausgeführt werden, die CORS unterstützen.
