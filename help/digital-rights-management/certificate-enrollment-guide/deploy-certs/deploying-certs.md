---
title: Bereitstellen von Zertifikaten
description: Bereitstellen von Zertifikaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Bereitstellen von Zertifikaten{#deploy-certificates}

Um zu vermeiden, dass das PFX-Kennwort in unverschlüsseltem Text auf dem Lizenzserver verfügbar ist, erfordern die Referenzimplementierung und der Adobe Primetime DRM-Server für geschütztes Streaming, dass das Kennwort verschlüsselt wird, wenn es in der Konfigurationsdatei angegeben ist. Siehe *Verwenden der Primetime-DRM-Referenzimplementierungen* oder *Verwenden des Primetime-DRM-Servers* für geschütztes Streaming für Anweisungen zum Ausführen der Rüstungswerkzeuge. Jedes dieser beinhaltet ein eigenes Rammble-Dienstprogramm, und die verschlüsselten Kennwörter sind zwischen diesen beiden License Server-Implementierungen nicht austauschbar.

Informationen zum Bereitstellen der Zertifikate und des verworfenen Kennworts auf Ihrem Lizenzserver finden Sie unter *Verwenden der Primetime-DRM-Referenzimplementierungen* oder *Verwenden des Primetime-DRM-Servers für geschütztes Streaming*.
