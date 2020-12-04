---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.
seo-description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.
seo-title: Wiedergabe und Failover
title: Wiedergabe und Failover
uuid: 7bbca3fe-88a3-4384-9a63-eb164c956a75
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.

>[!IMPORTANT]
>
>Primetime kann nicht vor Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen.

Das Primetime-Streaming bietet Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Serverausfällen oder Betriebsausfällen zu schützen, was eine bessere Anzeige ermöglicht. Trotz Übertragungsproblemen implementiert TVSDK einen Failover-Schutz, um die Wiedergabe-Unterbrechungen zu minimieren und eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Mediensatz, wenn vollständige Darstellungen oder Fragmente nicht verfügbar sind.