---
title: Verbesserte Lizenzverkettung
description: Verbesserte Lizenzverkettung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Verbesserte Lizenzverkettung {#enhanced-license-chaining}

Sie können die verbesserte Lizenzketten verwenden, um eine Lizenz zu aktualisieren, indem Sie eine übergeordnete Stammlizenz für die Batch-Aktualisierung von Lizenzen verwenden.

Primetime DRM 2.0 unterstützt Lizenzketten, bei denen sowohl die Leaf- als auch die Root-Lizenzen an einen bestimmten Computer gebunden sind. Primetime DRM 3.0 und höher unterstützt erweiterte Lizenzketten, bei denen ein Blatt an eine Stammlizenz gebunden ist und nur die Stammlizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten einer Leaf-Lizenz in den Inhalt. Der Client muss nur die Root-Lizenz vom Lizenzserver erwerben, um den geschützten Inhalt nutzen zu können.

Wenn Sie die erweiterte Lizenzverkettung aktivieren möchten, müssen Sie einer Primetime DRM-Richtlinie einen Root-Verschlüsselungsschlüssel zuweisen. Der Root-Verschlüsselungsschlüssel wird verwendet, um die Leaf-Lizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE]
>
>Erweiterte Lizenzketten werden von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzketten unterstützen, kann der Lizenzserver diesem Client weiterhin eine Lizenz erteilen, indem er die Lizenzketten verwendet, die von Primetime DRM 2.0 unterstützt werden.

Anwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen durch Herunterladen einer einzigen Root-Lizenz zu aktualisieren. Implementieren Sie beispielsweise Abonnementmodelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes besteht darin, dass Benutzer nur eine einzige Lizenz erwerben müssen, um alle ihre Abonnementlizenzen zu aktualisieren.
