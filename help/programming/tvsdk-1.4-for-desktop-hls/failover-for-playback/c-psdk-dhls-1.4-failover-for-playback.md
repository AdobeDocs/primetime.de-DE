---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität des Mediums lokal wiedergegeben wird.
title: Wiedergabe und Failover
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass bei der Remote-Wiedergabe möglicherweise nicht die Qualität des Mediums lokal wiedergegeben wird.

Primetime kann nicht vor solchen Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen. Das Primetime-Streaming bietet jedoch einen Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Serverausfällen oder Betriebsausfällen zu schützen, was eine bessere Benutzererfahrung ermöglicht. TVSDK implementiert Failover-Schutz, um Unterbrechungen bei der Wiedergabe zu minimieren und trotz Übertragungsproblemen eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Mediensatz, wenn vollständige Darstellungen oder Fragmente nicht verfügbar sind.
