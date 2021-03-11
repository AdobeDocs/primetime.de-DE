---
description: Jeder Einsatz von Adobe Primetime DRM besteht aus zwei wichtigen Schritten an verschiedenen Stellen des Workflows. Die Inhaltsvorbereitung muss einmal pro Asset durchgeführt werden und führt zur Erstellung geschützter Inhalte. Die Inhaltsakquise erfolgt mehrmals, einmal für jeden Verbraucher, der dieses geschützte Asset sehen möchte.
title: Inhaltsvorbereitung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Inhaltsvorbereitung{#content-preparation}

Jeder Einsatz von Adobe Primetime DRM besteht aus zwei wichtigen Schritten an verschiedenen Stellen des Workflows. Die Inhaltsvorbereitung muss einmal pro Asset durchgeführt werden und führt zur Erstellung geschützter Inhalte. Die Inhaltsakquise erfolgt mehrmals, einmal für jeden Verbraucher, der dieses geschützte Asset sehen möchte.

Bevor Sie Inhalte für die Distribution bereitstellen, müssen Sie zunächst die Inhalte in Ihrem Videoformat kodieren, eine oder mehrere Richtlinien erstellen, die Nutzungsregeln für die Inhalte festlegen, und die Inhalte mit dem Adobe Primetime DRM SDK verpacken.

Die Schritte zum Kodieren, Verpacken und Verteilen von Inhalten sind wie folgt:

1. Kodieren Sie den Inhalt in Ihrem gewünschten Videoformat mit Kodierungstools, die in der Adobe oder von Dritten verfügbar sind.
1. Erstellen Sie Richtlinien, die die Nutzungsregeln festlegen, unter denen die Ansicht der Inhalte für die Benutzer möglich ist.

   Eine Richtlinie ist der Container für die Regeln und Einschränkungen, die bestimmen, wie, wann und wo geschützte Inhalte von Verbrauchern angezeigt werden können.

   Für den Packager ist mindestens eine Richtlinie mit mindestens einer Nutzungsregel erforderlich. Sie können die Nutzungsregel überschreiben und zusätzliche Nutzungsregeln hinzufügen, wenn der Lizenzserver die Lizenz generiert.

1. Verpacken Sie den Inhalt und geben Sie an, welche Richtlinien angewendet werden sollen.

   Primetime DRM SDK verschlüsselt den Inhalt mit einem Content Encryption Key (CEK) und bindet eine oder mehrere Richtlinien an den Inhalt. Das Ergebnis ist eine *geschützte Inhaltsdatei *die nur von einem Benutzer wiedergegeben werden kann, der eine Lizenz vom entsprechenden License Server erhalten hat.

   Während der Verpackung wird der Inhalt mit dem CEK verschlüsselt. Das CEK wird mit dem öffentlichen Lizenzserver-Schlüssel verschlüsselt und zusammen mit den Richtlinien in die Primetime-DRM-Metadaten aufgenommen. Die Primetime-DRM-Metadaten werden mit dem privaten Schlüssel von Packager signiert und die Metadaten werden in den geschützten Inhalt eingefügt.

1. Bereitstellung geschützter Inhalte für die Verteilung an Verbraucher.

   Der geschützte Inhalt wird in der Regel über ein CDN (Content Distribution Network) verteilt. Das CDN kann jeden von der Client-Laufzeit unterstützten Mechanismus verwenden, z. B. Flash Media Server, Adobe-HTTP Dynamic Streaming für das Streaming mit mehreren Bitraten oder einen HTTP-Webserver für das progressive Herunterladen.

