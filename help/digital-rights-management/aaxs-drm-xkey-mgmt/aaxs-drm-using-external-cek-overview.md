---
description: Kunden können DRM (Adobe Access, AAXS) mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.
seo-description: Kunden können DRM (Adobe Access, AAXS) mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.
seo-title: Adobe Access DRM External CEK Überblick
title: Adobe Access DRM External CEK Überblick
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Adobe Access DRM External CEK Overview {#adobe-access-drm-external-cek-overview}

Kunden können DRM (Adobe Access, AAXS) mit ihren eigenen Content Key Management Systems (CKMS) mit der Funktion External CEK verwenden.

DRM (Adobe Access, AAXS) verhindert standardmäßig die direkte Verarbeitung von Schlüsseln, Zertifikaten und DRM-Metadaten während des Verpackungsvorgangs. Das AAXS Java SDK generiert während der Verpackungszeit automatisch einen zufälligen Content Encryption Key (CEK) und verwendet ihn zum Verschlüsseln des Inhalts. Anschließend verschlüsselt das SDK das CEK selbst und fügt es in die Metadaten des Inhalts ein. Zum Zeitpunkt der Lizenzausgabe benötigt der AAXS-Server nur seinen privaten AAXS-Lizenzserver-Schlüssel, um von den Metadaten aus auf das CEK zuzugreifen, um eine Lizenz zu generieren.
