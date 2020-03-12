---
description: Kunden können Adobe Access (AAXS) DRM mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.
seo-description: Kunden können Adobe Access (AAXS) DRM mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.
seo-title: Übersicht über Adobe Access DRM External CEK
title: Übersicht über Adobe Access DRM External CEK
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97

---


# Übersicht über Adobe Access DRM External CEK {#adobe-access-drm-external-cek-overview}

Kunden können Adobe Access (AAXS) DRM mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.

Mit Adobe Access (AAXS) DRM wird standardmäßig die Notwendigkeit abstrahiert, Schlüssel, Zertifikate und DRM-Metadaten während des Paketervorgangs direkt zu verarbeiten. Das AAXS Java SDK generiert während der Verpackungszeit automatisch einen zufälligen Content Encryption Key (CEK) und verwendet ihn zum Verschlüsseln des Inhalts. Anschließend verschlüsselt das SDK das CEK selbst und fügt es in die Metadaten des Inhalts ein. Zum Zeitpunkt der Lizenzausgabe benötigt der AAXS-Server nur seinen privaten AAXS-Lizenzserver-Schlüssel, um von den Metadaten aus auf das CEK zuzugreifen, um eine Lizenz zu generieren.
