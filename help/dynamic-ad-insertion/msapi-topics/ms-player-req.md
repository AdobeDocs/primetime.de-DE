---
description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.
seo-description: Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.
seo-title: Anforderungen an Videoplayer
title: Anforderungen an Videoplayer
uuid: 29593d67-2901-4d9e-a08f-23c8a7667283
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Anforderungen an Videoplayer {#video-player-requirements}

Alle Videoplayer müssen Funktionen bereitstellen, auf die der Manifestserver zum Einfügen von Anzeigen und zur Aktivierung der Anzeigenverfolgung angewiesen ist.

Um die Primetime-Anzeigen-Einfüge-API verwenden zu können, muss ein Videoplayer Folgendes erfüllen:

* Kann die Position des Abspielkopfs verfolgen, während der Inhalt wiedergegeben wird.
* Kann Tracking-URLs zu den angegebenen Zeiten anfordern.
* Wird auf einer Geräteplattform ausgeführt, die HLS v3 oder höher unterstützt, einschließlich:

   * PTS-Diskontinuitäten, gekennzeichnet durch `EXT-X-DISCONTINUITY` -Tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Wird auf einer Plattform ausgeführt, die HTTP-Umleitungen und das Parsen von JSON unterstützt.
* Wird auf einer Plattform ausgeführt, die CORS unterstützt.