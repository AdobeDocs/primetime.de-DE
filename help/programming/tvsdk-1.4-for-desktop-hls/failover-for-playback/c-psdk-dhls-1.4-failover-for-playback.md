---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.
title: Wiedergabe und Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität der Medien lokal wiedergegeben wird.

Primetime kann nicht vor solchen Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen. Primetime-Streaming bietet jedoch einen Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Server-Fehlern oder Betriebsausfällen zu schützen, wodurch das Erlebnis für Viewer verbessert wird. TVSDK implementiert einen Failover-Schutz, um Unterbrechungen der Wiedergabe zu minimieren und trotz Übertragungsproblemen eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Medienset, wenn vollständige Ausgabedarstellungen oder Fragmente nicht verfügbar sind.
