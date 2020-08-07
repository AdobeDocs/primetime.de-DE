---
seo-title: Enhanced license chaining
title: Enhanced license chaining
uuid: 5e4e825a-de84-4ab2-a652-02cc03153957
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Enhanced license chaining {#enhanced-license-chaining}

Sie können erweiterte Lizenzketten verwenden, um eine Lizenz zu aktualisieren, indem Sie eine übergeordnete Stammlizenz für die Batch-Aktualisierung von Lizenzen verwenden.

Primetime DRM 2.0 unterstützt Lizenzketten, bei denen die Blatt- und Root-Lizenzen an einen bestimmten Computer gebunden sind. Primetime DRM 3.0 und höher unterstützt erweiterte Lizenzketten, bei denen ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten einer Laublizenz in den Inhalt, und der Client muss die Stammlizenz nur vom Lizenzserver erwerben, um den geschützten Inhalt zu nutzen.

Wenn Sie die erweiterte Lizenzketten aktivieren möchten, müssen Sie einer Primetime-DRM-Richtlinie einen Root-Verschlüsselungsschlüssel zuweisen. Der Stamm-Verschlüsselungsschlüssel wird verwendet, um die Blattlizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE]
>
>Verbesserte Lizenzketten werden von Primetime DRM-Clients Version 3.0 oder höher unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzverkettung unterstützen, kann der Lizenzserver diesem Client weiterhin eine Lizenz ausstellen, indem er die Lizenzverkettung verwendet, die von Primetime DRM 2.0 unterstützt wird.

Verwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen zu aktualisieren, indem Sie eine einzige Root-Lizenz herunterladen. Implementieren Sie beispielsweise Abonnement-Modelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes besteht darin, dass die Nutzer nur eine einzige Lizenz erwerben müssen, um alle Abonnement-Lizenzen zu aktualisieren.
