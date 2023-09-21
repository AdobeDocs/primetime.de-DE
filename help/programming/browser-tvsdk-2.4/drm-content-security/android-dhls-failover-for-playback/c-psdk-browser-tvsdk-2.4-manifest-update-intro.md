---
description: Browser TVSDK kann geänderte Wiedergabeinformationen in Master-m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen während der Stream-Wiedergabe aktualisieren. Browser TVSDK unterstützt einen dynamischen Satz von Bitratenprofilen, wenn die Profile im Master-Manifest angezeigt oder ausgeblendet werden, einschließlich nicht überlappender Profil-Bitraten zwischen Aktualisierungen.
title: Update des Live-Master-Manifests
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Update des Live-Master-Manifests{#live-master-manifest-update}

Browser TVSDK kann geänderte Wiedergabeinformationen in Master-m3u8-Manifesten für Live-Streaming erkennen und die Wiedergabeinformationen während der Stream-Wiedergabe aktualisieren. Browser TVSDK unterstützt einen dynamischen Satz von Bitratenprofilen, wenn die Profile im Master-Manifest angezeigt oder ausgeblendet werden, einschließlich nicht überlappender Profil-Bitraten zwischen Aktualisierungen.

Die folgenden Funktionen werden unterstützt:

* Anzahl der Profile (erhöhen oder verringern)
* Profil-Bitraten (überlappend oder nicht überlappend)
* Profile mit URLs auf denselben (oder unterschiedlichen) Servern
* Jede Failover-Struktur

Alle folgenden Bedingungen müssen erfüllt sein:

* Stream ist live.
* Sowohl die Zeit als auch das eTag ändern sich.
* Alle Ausgabedarstellungsinformationen bleiben gleich (mit der Ausnahme, dass URLs variieren können).
* Die Informationen zum DRM-Zugriff bleiben unverändert.
* Segmente werden um dieselben PTS- und Frame-Grenzen in einem kleinen Fehlerbereich gebündelt.
