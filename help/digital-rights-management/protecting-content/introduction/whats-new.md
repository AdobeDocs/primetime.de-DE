---
description: Adobe Primetime DRM ist ein fortschrittliches Digital Rights Management (DRM) und Inhaltsschutz für hochwertige audiovisuelle Inhalte. In Anwendungen, die die Erstellung von Java-APIs unterstützen, können Sie das Primetime DRM-SDK verwenden, um DRM-Richtlinien anzugeben, diese Richtlinien auf Inhalte anzuwenden und diese Inhalte zu verschlüsseln.
seo-description: Adobe Primetime DRM ist ein fortschrittliches Digital Rights Management (DRM) und Inhaltsschutz für hochwertige audiovisuelle Inhalte. In Anwendungen, die die Erstellung von Java-APIs unterstützen, können Sie das Primetime DRM-SDK verwenden, um DRM-Richtlinien anzugeben, diese Richtlinien auf Inhalte anzuwenden und diese Inhalte zu verschlüsseln.
seo-title: Neue Funktionen in Adobe Primetime DRM
title: Neue Funktionen in Adobe Primetime DRM
uuid: 3c8da594-a231-4496-bffc-130775ecae50
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Neue Funktionen in Adobe Primetime DRM{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM ist ein fortschrittliches Digital Rights Management (DRM) und Inhaltsschutz für hochwertige audiovisuelle Inhalte. In Anwendungen, die die Erstellung von Java-APIs unterstützen, können Sie das Primetime DRM-SDK verwenden, um DRM-Richtlinien anzugeben, diese Richtlinien auf Inhalte anzuwenden und diese Inhalte zu verschlüsseln.

>[!NOTE]
>
>Primetime DRM wurde früher Adobe Access genannt, und davor, Flash Access.

Im Folgenden finden Sie einen Überblick über den Inhaltsschutz:

1. Verwenden Sie die DRM Java-APIs, um DRM-Richtlinieneigenschaften und Verschlüsselungsparameter festzulegen.
1. Erstellen Sie eine DRM-Richtlinie, die die Benutzerrollen für alle Inhalte beschreibt.

   Sie können beliebig viele DRM-Richtlinien erstellen. Die meisten Benutzer erstellen eine kleine Anzahl von Richtlinien und wenden sie dann auf viele Dateien an.
1. Verpacken Sie eine Mediendatei.

   *`Packaging a file`* bedeutet, dass Sie die Datei verschlüsseln und dann eine DRM-Richtlinie auf die Datei anwenden.
1. Implementieren Sie den Lizenzserver, um dem Benutzer eine Lizenz auszustellen.

Nach Abschluss dieser Schritte können Sie Ihre verschlüsselten Inhalte bereitstellen. Nach der Bereitstellung kann ein Client eine Lizenz vom Lizenzserver anfordern und den Inhalt nach Erhalt abspielen.

Das Primetime-DRM-SDK stellt eine Java-API zum Durchführen dieser Aufgaben bereit. Das SDK enthält Referenzimplementierungen des Lizenzservers und Befehlszeilenwerkzeuge, die beide auf den DRM SDK Java APIs basieren.

Die unten beschriebenen Funktionen sind in dieser Version neu.

## Neue Funktionen {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **Hard Stopp -** Sie können festlegen, ob die Wiedergabe am Ende eines Wiedergabefensters beendet oder fortgesetzt wird.
* **Auflösungsabhängige Ausgabesteuerelemente -** Sie können Ausgabebeschränkungen basierend auf Pixelauflösungen festlegen.
* **Anonymisierung von License Server-Antworten -** Zur Verbesserung der Privatsphäre mit Primetime DRM License Server-Protokollen wird die Seriennummer des Transportzertifikats für die Antwort des Lizenzservers auf unterstützende Clients Nullen zugewiesen.

