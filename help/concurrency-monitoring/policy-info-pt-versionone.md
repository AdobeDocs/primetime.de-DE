---
title: Richtlinienerklärungspunkt
description: Richtlinienerklärungspunkt
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---



# Richtlinienerklärungspunkt {#pip}

>[!NOTE]
>
>Diese Seite wird nicht mehr unterstützt, da sie für die vorherige API-Version gilt, die nicht mehr für neue Integrationen empfohlen wird

Das folgende Diagramm zeigt den Fluss, falls sich der Kunde für die **Richtlinienerklärungspunkt**; in diesem Fall wird CM lediglich zur Abfrage der Aktivität verwendet und die gesamte Zugriffslogik ist in die Clientanwendung eingebettet):

![](assets/pip-workflow.png)



Das folgende Diagramm zeigt, wie die Stream-Zählung für einen Benutzer funktioniert, der Inhalte von zwei Geräten aus betrachtet.

![](assets/pip-sequence.png)

Kurz gesagt, der normale Nachrichtenfluss ist wie folgt:

1. Zunächst wird für einen Benutzer, der den Dienst noch nie verwendet hat, eine Webseite geladen bzw. eine Anwendung geöffnet, in der eine instrumentierte Anwendung für den Dienst zur Überwachung der Parallelität einen Aufruf zur Sitzungsinitialisierung sendet.
1. Der Concurrency Monitoring Service gibt die neue Stream-Ressource für Heartbeats sowie die aktuelle Benutzeraktivität zurück.
1. Während der Videowiedergabe führt die instrumentierte Anwendung Heartbeat-Aufrufe an den Dienst für die Überwachung der Parallelität durch und zeigt an, dass der Benutzer derzeit ein Video nutzt.
1. Zu jedem anderen Zeitpunkt können andere instrumentierte Anwendungen Statusabfrageaufrufe an den Dienst für die Überwachung der Parallelität senden, wodurch die aktuelle Benutzeraktivität zurückgegeben wird.
1. Am Ende der Videowiedergabe kann die instrumentierte Anwendung einen Heartbeat-Aufruf mit &quot;event=stop&quot;durchführen, was bedeutet, dass das Video gestoppt wurde und der aktuelle Stream nicht mehr als aktiver Stream gezählt werden sollte.

