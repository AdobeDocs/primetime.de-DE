---
description: Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität der lokal wiedergegebenen Medien aufweist.
title: Wiedergabe und Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Übersicht {#playback-and-failover-overview}

Streaming über das Internet erfordert eine konstante und stabile Verbindung, um einen Stream von einem Remote-Server wiederzugeben. Die Variabilität der Internet-Verbindung oder Streaming-Wiedergabe eines Viewers bedeutet jedoch, dass die Remote-Wiedergabe möglicherweise nicht die Qualität der lokal wiedergegebenen Medien aufweist.

>[!IMPORTANT]
>
>Primetime kann nicht vor Fehlern wie einem ISP-Ausfall oder einer Kabeltrennung schützen.

Das Primetime-Streaming bietet Failover-Schutz, um die Wiedergabe vor bestimmten Remote-Server-Fehlern oder Betriebsausfällen zu schützen, was eine bessere Anzeige ermöglicht. Trotz Übertragungsproblemen implementiert TVSDK einen Failover-Schutz, um Wiedergabeunterbrechungen zu minimieren und eine nahtlose Wiedergabe zu erzielen. Der Videoplayer wechselt automatisch zu einem Backup-Medienset, wenn vollständige Ausgabedarstellungen oder Fragmente nicht verfügbar sind.
