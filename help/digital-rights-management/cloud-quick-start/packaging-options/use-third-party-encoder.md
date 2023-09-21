---
title: Verwenden eines Kodierers eines Drittanbieters
description: Verwenden eines Kodierers eines Drittanbieters
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Verwenden eines Kodierers eines Drittanbieters{#use-a-third-party-encoder}

Einige Kunden verfügen möglicherweise bereits über eine Pipeline zur Inhaltsvorbereitung, die einen Hardware- oder Software-Videokodierer (oder -Adobe Media Server) verwendet. Ist dies der Fall, kann jedes Produkt, das derzeit DRM-geschützte Inhalte von Primetime erstellen kann, Inhalte für Primetime Cloud DRM verpacken, indem dieselben Konfigurationseinstellungen wie das Primetime Cloud DRM Protection Kit verwendet werden. Die erforderlichen Informationen können aus einer der vorhandenen Konfigurationsdateien im Kit abgerufen werden: [!DNL config_hls.xml] oder [!DNL config_hds.xml].

Die relevanten Konfigurationselemente sind:

* Lizenzserver-URL
* Key Server URL
* Lizenzserver-Zertifikat
* Transportbescheinigung
