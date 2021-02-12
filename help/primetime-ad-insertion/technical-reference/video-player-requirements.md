---
description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.
seo-description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.
seo-title: Anforderungen an Videoplayer
title: Anforderungen an Videoplayer
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '138'
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
* Internetbasierte Player müssen auf Plattformen ausgeführt werden, die CORS unterstützen.