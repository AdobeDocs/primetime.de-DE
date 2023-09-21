---
description: Jeder Einsatz von Adobe Primetime DRM besteht aus zwei wichtigen Schritten an verschiedenen Stellen des Workflows. Die Inhaltsvorbereitung muss einmal pro Asset erfolgen und führt zur Erstellung geschützter Inhalte. Die Inhaltsakquise erfolgt mehrmals, einmal für jeden Verbraucher, der dieses geschützte Asset sehen möchte.
title: Inhaltsvorbereitung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Inhaltsvorbereitung{#content-preparation}

Jeder Einsatz von Adobe Primetime DRM besteht aus zwei wichtigen Schritten an verschiedenen Stellen des Workflows. Die Inhaltsvorbereitung muss einmal pro Asset erfolgen und führt zur Erstellung geschützter Inhalte. Die Inhaltsakquise erfolgt mehrmals, einmal für jeden Verbraucher, der dieses geschützte Asset sehen möchte.

Bevor Sie Inhalte für die Verteilung verfügbar machen, müssen Sie zunächst den Inhalt im Videoformat kodieren, eine oder mehrere Richtlinien erstellen, die Nutzungsregeln für den Inhalt angeben, und den Inhalt mit dem Adobe Primetime DRM SDK verpacken.

Die Schritte zum Kodieren, Verpacken und Verteilen von Inhalten lauten wie folgt:

1. Kodieren Sie den Inhalt im gewünschten Videoformat mithilfe von Kodierungs-Tools, die von Adobe oder von Drittanbietern verfügbar sind.
1. Erstellen Sie Richtlinien, die die Nutzungsregeln festlegen, unter denen Verbraucher den Inhalt anzeigen können.

   Eine Richtlinie ist der Container für die Regeln und Einschränkungen, die bestimmen, wie, wann und wo geschützte Inhalte von Verbrauchern angezeigt werden können.

   Der Packager erfordert mindestens eine Richtlinie mit mindestens einer Nutzungsregel. Sie können die Nutzungsregel überschreiben und zusätzliche Nutzungsregeln hinzufügen, wenn der Lizenzserver die Lizenz generiert.

1. Verpacken Sie den Inhalt und geben Sie an, welche Richtlinien angewendet werden sollen.

   Das Primetime DRM SDK verschlüsselt den Inhalt mit einem Inhaltsverschlüsselungsschlüssel (Content Encryption Key, CEK) und bindet eine oder mehrere Richtlinien an den Inhalt. Das Ergebnis ist eine *geschützte Inhaltsdatei *, die nur von einem Verbraucher wiedergegeben werden kann, der eine Lizenz vom entsprechenden Lizenzserver erhalten hat.

   Während der Verpackung wird der Inhalt mit dem CEK verschlüsselt. Das CEK wird mithilfe des öffentlichen Lizenzserver-Schlüssels verschlüsselt und zusammen mit den Richtlinien in die Primetime-DRM-Metadaten aufgenommen. Die Primetime-DRM-Metadaten werden mit dem privaten Schlüssel Packager signiert und die Metadaten werden in den geschützten Inhalt aufgenommen.

1. Bereitstellung geschützter Inhalte für den Vertrieb an Verbraucher.

   Der geschützte Inhalt wird in der Regel über ein CDN (Content Distribution Network) verteilt. Das CDN kann jeden von der Client-Laufzeitumgebung unterstützten Mechanismus verwenden, z. B. Flash Media Server, Adobe-HTTP Dynamic Streaming für das Streaming mit mehreren Bitraten oder einen HTTP-Webserver für den progressiven Download.
