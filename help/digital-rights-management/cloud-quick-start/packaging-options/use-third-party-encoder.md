---
seo-title: Verwenden eines Drittanbieter-Encoder
title: Verwenden eines Drittanbieter-Encoder
uuid: 8649303c-b8e6-4c02-a8ad-5734af850bfe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwenden eines Drittanbieter-Encoder{#use-a-third-party-encoder}

Einige Kunden verfügen möglicherweise bereits über eine Pipeline zur Inhaltsvorbereitung, die einen Hardware- oder Software-Video-Encoder (oder Adobe Media Server) verwendet. Ist dies der Fall, kann jedes Produkt, das derzeit DRM-geschützte Inhalte mit Primetime erstellen kann, Inhalte für Primetime Cloud DRM verpacken, indem dieselben Konfigurationseinstellungen wie das Primetime Cloud DRM Protection Kit verwendet werden. Die erforderlichen Informationen können aus einer der vorhandenen Konfigurationsdateien im Kit abgerufen werden: [!DNL config_hls.xml] oder [!DNL config_hds.xml].

Die relevanten Konfigurationselemente sind:

* Lizenzserver-URL
* Key Server-URL
* Lizenzserverzertifikat
* Transportbescheinigung

