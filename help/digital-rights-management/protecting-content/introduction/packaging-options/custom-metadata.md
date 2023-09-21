---
title: Benutzerspezifische Metadaten
description: Benutzerspezifische Metadaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Benutzerspezifische Metadaten {#custom-metadata}

Verwenden Sie dies, um benutzerdefinierte Schlüssel/Wert-Paare zu Inhaltsmetadaten hinzuzufügen, die von der Serveranwendung interpretiert werden können.

Mit dem Metadatenformat für Primetime-DRM-Inhalte können Sie benutzerdefinierte Schlüssel/Wert-Paare zur Paketierungszeit einbeziehen. Diese benutzerdefinierten Metadaten können dann vom Lizenzserver während der Lizenzerteilung verarbeitet werden. Die Metadaten sind separat von einer Primetime-DRM-Richtlinie und können für jeden Inhaltsabschnitt eindeutig sein.

Anwendungsbeispiel: Während einer Beta-Phase können Sie die benutzerdefinierte Eigenschaft einbeziehen `Release:BETA` zum Zeitpunkt der Verpackung. Lizenzserver können während der Beta-Phase Lizenzen für diesen Inhalt bereitstellen. Nach Ablauf der Beta-Zeit verbieten die Lizenzserver jedoch den Zugriff auf den Inhalt.
