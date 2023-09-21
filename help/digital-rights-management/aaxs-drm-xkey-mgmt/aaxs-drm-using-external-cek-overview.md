---
description: Kunden können mit der externen CEK-Funktion Adobe Access (AAXS) DRM mit ihren eigenen Content Key Management Systems (CKMS) verwenden.
title: Adobe Access DRM External CEK - Überblick
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Adobe Access DRM External CEK - Überblick {#adobe-access-drm-external-cek-overview}

Kunden können mit der externen CEK-Funktion Adobe Access (AAXS) DRM mit ihren eigenen Content Key Management Systems (CKMS) verwenden.

Adobe Access (AAXS) DRM stellt standardmäßig die Notwendigkeit dar, Schlüssel, Zertifikate und DRM-Metadaten während des Inhaltspaketprozesses direkt zu verarbeiten. Das AXS Java SDK generiert während der Verpackungszeit automatisch einen zufälligen Inhaltsverschlüsselungsschlüssel (CEK) und verschlüsselt den Inhalt. Als Nächstes verschlüsselt das SDK das CEK selbst und fügt es in die Metadaten des Inhalts ein. Zum Zeitpunkt der Lizenzausgabe benötigt der AXS-Server nur seinen privaten AXS-Lizenzserver-Schlüssel, um von den Metadaten aus auf den CEK zuzugreifen und eine Lizenz zu generieren.
