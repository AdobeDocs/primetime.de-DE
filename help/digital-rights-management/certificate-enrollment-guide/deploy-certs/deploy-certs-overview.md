---
title: Übersicht über die Bereitstellung von Zertifikaten
description: Übersicht über die Bereitstellung von Zertifikaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Übersicht {#deploy-certificates-overview}

Um den Adobe Primetime DRM-Eigenschaftendateien Zertifikate hinzuzufügen, konvertieren Sie die PKCS#7-Datei mithilfe des privaten Schlüssels in eine PFX-Datei und generieren Sie entweder eine PEM- oder eine DER-Datei.

* Wenn eine Berechtigung (Zertifikat und privater Schlüssel) erforderlich ist, benötigen die Primetime DRM-Befehlszeilen-Tools und der Adobe HTTP Dynamic Streaming Packager eine PFX-Datei. SDK, Referenzimplementierung und Primetime DRM Server for Protected Streaming können eine PFX-Datei akzeptieren und auch eine auf einem HSM gespeicherte Berechtigung verwenden.
* Wenn nur ein Zertifikat erforderlich ist, können die meisten Primetime-DRM-Komponenten eine PEM-Datei, eine DER-Datei oder ein Zertifikat auf einem HSM verwenden. Der Adobe HTTP Dynamic Streaming Packager akzeptiert nur DER-Dateien für Zertifikate.
