---
description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.
title: Anforderungen an Videoplayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Anforderungen für Videoplayer {#video-player-requirements}

Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.

Um die Primetime-Anzeigen-Einfüge-API verwenden zu können, muss ein Videoplayer Folgendes erfüllen:

* Kann die Position des Abspielkopfs verfolgen, während der Inhalt wiedergegeben wird.
* Kann Tracking-URLs zu den angegebenen Zeiten anfordern.
* Wird auf einer Geräteplattform ausgeführt, die HLS v3 oder höher unterstützt, einschließlich:

   * PTS-Diskontinuitäten, wie durch `EXT-X-DISCONTINUITY`-Tags gekennzeichnet
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Wird auf einer Plattform ausgeführt, die HTTP-Umleitungen und das Parsen von JSON unterstützt.
* Wird auf einer Plattform ausgeführt, die CORS unterstützt.