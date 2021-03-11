---
title: Verwenden eines Drittanbieter-Encoder
description: Verwenden eines Drittanbieter-Encoder
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Einen Drittanbieter-Encoder verwenden{#use-a-third-party-encoder}

Einige Kunden verfügen möglicherweise bereits über eine Pipeline zur Inhaltsvorbereitung, die einen Hardware- oder Software-Video-Encoder (oder Adobe Mediums-Server) verwendet. Ist dies der Fall, kann jedes Produkt, das derzeit DRM-geschützte Inhalte mit Primetime erstellen kann, Inhalte für Primetime Cloud DRM verpacken, indem dieselben Konfigurationseinstellungen wie das Primetime Cloud DRM Protection Kit verwendet werden. Die erforderlichen Informationen können aus einer der vorhandenen Konfigurationsdateien im Kit abgerufen werden: [!DNL config_hls.xml] oder [!DNL config_hds.xml].

Die relevanten Konfigurationselemente sind:

* Lizenzserver-URL
* Key Server-URL
* Lizenzserverzertifikat
* Transportbescheinigung

