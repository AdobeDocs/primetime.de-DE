---
description: Browser TVSDK kann geänderte Wiedergabeinformationen in Übergeordnet m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen aktualisieren, während der Stream wiedergegeben wird. Browser TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile aus dem Übergeordnet-Manifest erscheinen oder verschwinden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.
seo-description: Browser TVSDK kann geänderte Wiedergabeinformationen in Übergeordnet m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen aktualisieren, während der Stream wiedergegeben wird. Browser TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile aus dem Übergeordnet-Manifest erscheinen oder verschwinden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.
seo-title: Live-Übergeordnet-Manifest-Update
title: Live-Übergeordnet-Manifest-Update
uuid: 4b918a73-dacf-465a-82d6-404c6bdb01f2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Live-Übergeordnet-Manifest-Update{#live-master-manifest-update}

Browser TVSDK kann geänderte Wiedergabeinformationen in Übergeordnet m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen aktualisieren, während der Stream wiedergegeben wird. Browser TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile aus dem Übergeordnet-Manifest erscheinen oder verschwinden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.

Die folgenden Funktionen werden unterstützt:

* Anzahl der Profil (Erhöhen oder verringern)
* Bitraten im Profil (Überschneidung oder Nichtüberschneidung)
* Profil mit URLs auf demselben (oder anderen) Server
* Jede Failover-Struktur

Alle folgenden Bedingungen müssen erfüllt sein:

* Stream ist live.
* Sowohl die Uhrzeit als auch das Tag ändern sich.
* Alle Darstellungsinformationen bleiben gleich (mit der Ausnahme, dass URLs variieren können).
* Die DRM-Zugriffsinformationen bleiben unverändert.
* Segmente werden in einem kleinen Fehlerbereich um dieselben PTS- und Frame-Begrenzungen gepackt.

