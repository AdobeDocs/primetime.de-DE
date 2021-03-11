---
description: Browser TVSDK kann geänderte Wiedergabeinformationen in Übergeordnet m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen aktualisieren, während der Stream wiedergegeben wird. Browser TVSDK unterstützt einen dynamischen Satz von Bitrate-Profilen, wenn die Profile aus dem Übergeordnet-Manifest erscheinen oder verschwinden, einschließlich nicht überlappender Profil-Bitraten zwischen Updates.
title: Live-Übergeordnet-Manifest-Update
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
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

