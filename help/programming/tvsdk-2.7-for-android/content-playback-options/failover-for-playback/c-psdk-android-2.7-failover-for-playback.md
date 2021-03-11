---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.
title: Wiedergabe und Failover
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.

>[!IMPORTANT]
>
>Primetime kann nicht vor Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen.

Das Primetime-Streaming bietet Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Serverausfällen oder Betriebsausfällen zu schützen, was eine bessere Anzeige ermöglicht. Trotz Übertragungsproblemen implementiert TVSDK einen Failover-Schutz, um die Wiedergabe-Unterbrechungen zu minimieren und eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Mediensatz, wenn vollständige Darstellungen oder Fragmente nicht verfügbar sind.