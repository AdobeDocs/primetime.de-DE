---
title: Zertifikate bereitstellen
description: Zertifikate bereitstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Zertifikate bereitstellen{#deploy-certificates}

Um zu vermeiden, dass das PFX-Kennwort im Klartext auf dem Lizenzserver verfügbar ist, müssen die Referenz-Implementierung und der Adobe Primetime DRM-Server für geschütztes Streaming das Kennwort verschlüsseln, wenn es in der Konfigurationsdatei angegeben ist. Informationen zum Ausführen der verwüstenden Dienstprogramme finden Sie unter Verwenden der Primetime-DRM-Referenzimplementierungen *oder* Verwenden des Primetime-DRM-Servers *für geschütztes Streaming.* Jedes dieser Programme enthält ein eigenes Dienstprogramm zum Verschlüsseln, und die verschlüsselten Kennwörter sind nicht zwischen diesen beiden License Server-Implementierungen austauschbar.

Informationen zum Bereitstellen der Zertifikate und des unverschlüsselten Kennworts auf Ihrem Lizenzserver finden Sie unter *Verwenden der Primetime-DRM-Referenzimplementierungen* oder *Verwenden des Primetime-DRM-Servers für geschütztes Streaming*.
