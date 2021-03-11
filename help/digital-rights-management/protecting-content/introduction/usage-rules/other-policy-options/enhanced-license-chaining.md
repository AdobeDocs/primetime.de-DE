---
title: Verbesserte Lizenzverkettung
description: Verbesserte Lizenzverkettung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Verbesserte Lizenzverkettung {#enhanced-license-chaining}

Sie können erweiterte Lizenzketten verwenden, um eine Lizenz zu aktualisieren, indem Sie eine übergeordnete Stammlizenz für die Batch-Aktualisierung von Lizenzen verwenden.

Primetime DRM 2.0 unterstützt Lizenzketten, bei denen die Blatt- und Root-Lizenzen an einen bestimmten Computer gebunden sind. Primetime DRM 3.0 und höher unterstützt erweiterte Lizenzketten, bei denen ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten einer Laublizenz in den Inhalt, und der Client muss die Stammlizenz nur vom Lizenzserver erwerben, um den geschützten Inhalt zu nutzen.

Wenn Sie die erweiterte Lizenzketten aktivieren möchten, müssen Sie einer Primetime-DRM-Richtlinie einen Root-Verschlüsselungsschlüssel zuweisen. Der Stamm-Verschlüsselungsschlüssel wird verwendet, um die Blattlizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE]
>
>Verbesserte Lizenzketten werden von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzverkettung unterstützen, kann der Lizenzserver diesem Client weiterhin eine Lizenz ausstellen, indem er die Lizenzverkettung verwendet, die von Primetime DRM 2.0 unterstützt wird.

Verwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen zu aktualisieren, indem Sie eine einzige Root-Lizenz herunterladen. Implementieren Sie beispielsweise Abonnement-Modelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes besteht darin, dass die Nutzer nur eine einzige Lizenz erwerben müssen, um alle Abonnement-Lizenzen zu aktualisieren.
