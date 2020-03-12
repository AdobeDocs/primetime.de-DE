---
seo-title: Verbesserte Lizenzverkettung
title: Verbesserte Lizenzverkettung
uuid: d11b0631-5dfb-42b8-b7ba-cfeb1da488be
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Verbesserte Lizenzverkettung {#enhanced-license-chaining}

Ermöglicht die Aktualisierung einer Lizenz mit einer übergeordneten Stammlizenz für die Batch-Aktualisierung von Lizenzen.

Von Adobe Access 2.0 unterstützte Lizenzverkettungen, bei denen sowohl die Blatt- als auch die Root-Lizenzen an einen bestimmten Computer gebunden sind. Adobe Access 3.0 unterstützt erweiterte Lizenzketten, bei denen ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Die verbesserte Lizenzketten unterstützt das Einbetten der Laublizenz in den Inhalt. Der Client muss die Stammlizenz nur vom Lizenzserver erwerben, um den geschützten Inhalt zu nutzen.

Um die erweiterte Lizenzketten zu aktivieren, wird der Richtlinie ein Stamm-Verschlüsselungsschlüssel zugewiesen. Der Stamm-Verschlüsselungsschlüssel wird verwendet, um die Blattlizenz kryptografisch an die Root-Lizenz zu binden.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die verbesserte Lizenzverkettung wird von Adobe Access-Clients ab Version 3.0 unterstützt. Wenn ein älterer Client eine Lizenz für Inhalte anfordert, die die erweiterte Lizenzverkettung unterstützen, kann der Lizenzserver diesem Client weiterhin eine Lizenz mit der von Adobe Access 2.0 unterstützten Lizenzketten ausstellen.

Verwendungsbeispiel: Verwenden Sie diese Option, um verknüpfte Lizenzen zu aktualisieren, indem Sie eine einzige Root-Lizenz herunterladen. Implementieren Sie beispielsweise Abonnement-Modelle, bei denen Inhalte wiedergegeben werden können, solange der Benutzer das Abonnement monatlich verlängert. Der Vorteil dieses Ansatzes liegt darin, dass die Nutzer nur eine einzige Lizenz erwerben müssen, um alle Abonnement-Lizenzen zu aktualisieren.
