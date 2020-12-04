---
seo-title: Übersicht über die Bereitstellung von Zertifikaten
title: Übersicht über die Bereitstellung von Zertifikaten
uuid: e6413f9f-69a5-4881-bb13-47a80cf32a48
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Übersicht {#deploy-certificates-overview}

Um den Adobe Primetime DRM-Eigenschaftendateien Zertifikate hinzuzufügen, konvertieren Sie die PKCS#7-Datei mit dem privaten Schlüssel in eine PFX-Datei und generieren Sie entweder eine PEM- oder eine DER-Datei.

* Wenn eine Berechtigung (Zertifikat und privater Schlüssel) erforderlich ist, benötigen die Primetime DRM-Befehlszeilenwerkzeuge und der Adobe HTTP Dynamic Streaming Packager eine PFX-Datei. SDK, Reference Implementation und Primetime DRM Server for Protected Streaming können eine PFX-Datei akzeptieren und auch eine auf einem HSM gespeicherte Berechtigung verwenden.
* Wenn nur ein Zertifikat erforderlich ist, können die meisten Primetime-DRM-Komponenten eine PEM-, DER- oder ein Zertifikat für ein HSM verwenden. Der Adobe HTTP Dynamic Streaming Packager akzeptiert nur DER-Dateien für Zertifikate.