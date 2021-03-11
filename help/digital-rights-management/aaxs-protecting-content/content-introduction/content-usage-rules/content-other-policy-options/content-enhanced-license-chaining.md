---
title: Verbesserte Lizenzverkettung
description: Verbesserte Lizenzverkettung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# Verbesserte Lizenzverkettung {#enhanced-license-chaining}

Ermöglicht die Aktualisierung einer Lizenz mit einer übergeordneten Stammlizenz für die Batch-Aktualisierung von Lizenzen.

Adobe Access 2.0 unterstützt Lizenzketten, in denen die Blatt- und Root-Lizenzen an einen bestimmten Computer gebunden sind. Adobe Access 3.0 unterstützt erweiterte Lizenzketten, bei denen ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten der Laublizenz in den Inhalt. Der Client muss die Stammlizenz nur vom Lizenzserver erwerben, um den geschützten Inhalt zu nutzen.

Um die erweiterte Lizenzketten zu aktivieren, wird der Richtlinie ein Stamm-Verschlüsselungsschlüssel zugewiesen. Der Stamm-Verschlüsselungsschlüssel wird verwendet, um die Blattlizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE]
>
>Die verbesserte Lizenzverkettung wird von Adobe Access Clients ab Version 3.0 unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzverkettung unterstützen, kann der Lizenzserver weiterhin eine Lizenz für diesen Client ausstellen, indem er Lizenzketten verwendet, die von Adobe Access 2.0 unterstützt werden.

Verwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen zu aktualisieren, indem Sie eine einzige Root-Lizenz herunterladen. Implementieren Sie beispielsweise Abonnement-Modelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes liegt darin, dass die Nutzer nur eine einzige Lizenz erwerben müssen, um alle Abonnement-Lizenzen zu aktualisieren.
