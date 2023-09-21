---
description: Adobe Primetime DRM ist eine fortschrittliche Digital Rights Management- und Inhaltsschutzlösung für hochwertige audiovisuelle Inhalte. In Anwendungen, die die Erstellung von Java-APIs unterstützen, können Sie das Primetime DRM SDK verwenden, um DRM-Richtlinien anzugeben, diese Richtlinien auf Inhalte anzuwenden und diese Inhalte zu verschlüsseln.
title: Neue Funktionen in Adobe Primetime DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Neue Funktionen in Adobe Primetime DRM{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM ist eine fortschrittliche Digital Rights Management- und Inhaltsschutzlösung für hochwertige audiovisuelle Inhalte. In Anwendungen, die die Erstellung von Java-APIs unterstützen, können Sie das Primetime DRM SDK verwenden, um DRM-Richtlinien anzugeben, diese Richtlinien auf Inhalte anzuwenden und diese Inhalte zu verschlüsseln.

>[!NOTE]
>
>Primetime DRM hieß früher Adobe Access, und davor war Flash Access.

Hier finden Sie eine allgemeine Anleitung zum Inhaltsschutz:

1. Verwenden Sie die DRM Java-APIs, um Eigenschaften und Verschlüsselungsparameter der DRM-Richtlinie festzulegen.
1. Erstellen Sie eine DRM-Richtlinie, die die Nutzungsrollen für Inhalte beschreibt.

   Sie können eine beliebige Anzahl von DRM-Richtlinien erstellen. Die meisten Benutzer erstellen eine kleine Anzahl von Richtlinien und wenden sie dann auf viele Dateien an.
1. Verpacken Sie eine Mediendatei.

   *`Packaging a file`* bedeutet, dass Sie die Datei verschlüsseln und dann eine DRM-Richtlinie auf die Datei anwenden.
1. Implementieren Sie den Lizenzserver, um dem Benutzer eine Lizenz zu erteilen.

Nach Abschluss dieser Schritte kann Ihr verschlüsselter Inhalt bereitgestellt werden. Nach der Bereitstellung kann ein Client eine Lizenz vom Lizenzserver anfordern und nach Erhalt den Inhalt wiedergeben.

Das Primetime DRM SDK stellt eine Java-API zum Ausführen dieser Aufgaben bereit. Das SDK enthält Referenzimplementierungen des Lizenzservers und Befehlszeilen-Tools, die beide auf den DRM SDK Java APIs basieren.

Die unten beschriebenen Funktionen sind in dieser Version neu.

## Neue Funktionen {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **Hard Stopp -** Sie können angeben, ob die Wiedergabe am Ende eines Wiedergabefensters beendet wird oder fortgesetzt wird.
* **Auflösungsabhängige Ausgabesteuerelemente -** Sie können Ausgabedarstellungen anhand von Pixelauflösungen festlegen.
* **Anonymisierung von Lizenzserver-Antworten -** Um den Datenschutz mit den Primetime DRM License Server-Protokollen zu verbessern, wird die Seriennummer des Transportzertifikats für die Antworten des Lizenzservers an unterstützende Clients nullt angezeigt.
