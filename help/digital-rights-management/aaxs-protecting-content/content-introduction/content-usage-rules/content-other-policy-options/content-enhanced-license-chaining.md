---
title: Verbesserte Lizenzverkettung
description: Verbesserte Lizenzverkettung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Verbesserte Lizenzverkettung {#enhanced-license-chaining}

Ermöglicht die Aktualisierung einer Lizenz mit einer übergeordneten Stammlizenz für die Batch-Aktualisierung von Lizenzen.

Adobe Access 2.0 unterstützte Lizenzketten, in denen sowohl die Leaf- als auch die Root-Lizenzen an einen bestimmten Computer gebunden sind. Adobe Access 3.0 unterstützt eine verbesserte Lizenzketten, bei denen ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten einer Leaf-Lizenz in den Inhalt. Der Client muss nur die Root-Lizenz vom Lizenzserver erwerben, um den geschützten Inhalt nutzen zu können.

Um die erweiterte Lizenzketten zu aktivieren, wird der Richtlinie ein Root-Verschlüsselungsschlüssel zugewiesen. Der Root-Verschlüsselungsschlüssel wird verwendet, um die Leaf-Lizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE]
>
>Die verbesserte Lizenzketten wird von Adobe Access Clients ab Version 3.0 unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzketten unterstützen, kann der Lizenzserver diesem Client weiterhin eine Lizenz für die Lizenzketten erteilen, die von Adobe Access 2.0 unterstützt werden.

Anwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen durch Herunterladen einer einzigen Root-Lizenz zu aktualisieren. Implementieren Sie beispielsweise Abonnementmodelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes besteht darin, dass Benutzer nur eine einzige Lizenzakquise vornehmen müssen, um alle ihre Abonnementlizenzen zu aktualisieren.
