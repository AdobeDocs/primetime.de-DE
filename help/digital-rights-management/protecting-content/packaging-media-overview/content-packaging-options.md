---
title: Paketoptionen
description: Paketoptionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---

# Paketoptionen{#packaging-options}

Für die Verpackung von Inhalten stehen Ihnen zahlreiche Optionen zur Verfügung. Sie können die Optionen im `DRMParameters` -Schnittstelle verwenden und die Klassen implementieren, die eine Schnittstelle bilden können. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert werden, finden Sie in den Beschreibungen der Befehlszeilenoptionen von Media Packager, die unter *Verwenden der Adobe Primetime DRM-Referenzimplementierungen*. Diese Optionen basieren auf der Java-API und stehen daher für die programmatische Nutzung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, partielle Verschlüsselung).
* Lizenzserver-URL, die der Client als Basis-URL für alle an den Lizenzserver gesendeten Anfragen verwendet
* Lizenzserver-Transportzertifikat
* Lizenzserver-Zertifikat zum Verschlüsseln des CEK
* Paketberechtigung für das Signieren von Metadaten
