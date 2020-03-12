---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.
seo-description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.
seo-title: Wiedergabe und Failover
title: Wiedergabe und Failover
uuid: 511f16b9-2b86-42c1-8d89-09b26534200b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server abspielen zu können. Die Variabilität der Internetverbindung oder der Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität des lokal wiedergegebenen Mediums aufweist.

>[!IMPORTANT]
>
>Primetime kann nicht vor Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen.

Primetime-Streaming bietet Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Serverausfällen oder Betriebsausfällen zu schützen, was eine bessere Anzeige ermöglicht. Trotz Übertragungsproblemen implementiert TVSDK einen Failover-Schutz, um die Wiedergabe-Unterbrechungen zu minimieren und eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Mediensatz, wenn vollständige Darstellungen oder Fragmente nicht verfügbar sind.