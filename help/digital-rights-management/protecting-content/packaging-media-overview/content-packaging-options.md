---
title: Verpackungsoptionen
description: Verpackungsoptionen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Verpackungsoptionen{#packaging-options}

Es stehen Ihnen zahlreiche Optionen zum Verpacken von Inhalten zur Verfügung. Sie können die Optionen in der `DRMParameters`-Schnittstelle angeben und die Klassen implementieren, die eine Schnittstelle ermöglichen. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert sind, finden Sie in den Beschreibungen der Media Packager-Befehlszeilenoptionen, die unter *Verwenden der Adobe Primetime DRM-Referenzimplementierungen* beschrieben werden. Diese Optionen basieren auf der Java-API und stehen daher zur programmatischen Nutzung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, teilweise Verschlüsselung).
* Lizenzserver-URL, die der Client als Basis-URL für alle an den Lizenzserver gesendeten Anforderungen verwendet
* Lizenzservertransportzertifikat
* Lizenzserverzertifikat zum Verschlüsseln des CEK
* Packager-Berechtigung zum Signieren von Metadaten

