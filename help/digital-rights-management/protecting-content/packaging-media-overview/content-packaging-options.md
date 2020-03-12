---
seo-title: Verpackungsoptionen
title: Verpackungsoptionen
uuid: 04244428-cb42-438a-8f16-91532c70ea60
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verpackungsoptionen{#packaging-options}

Es stehen Ihnen zahlreiche Optionen zum Verpacken von Inhalten zur Verfügung. Sie können die Optionen auf der `DRMParameters` Oberfläche angeben und die Klassen implementieren, die eine Schnittstelle ermöglichen. Mit diesen Klassen können Sie Signatur- und Schlüsselparameter festlegen sowie angeben, ob Audioinhalte, Videoinhalte oder Skriptdaten verschlüsselt werden sollen. Informationen dazu, wie diese in der Referenzimplementierung implementiert sind, finden Sie in den Beschreibungen der Befehlszeilenoptionen in Media Packager, die unter Verwenden der DRM-Referenzimplementierungen *von Adobe Primetime beschrieben werden*. Diese Optionen basieren auf der Java-API und stehen daher zur programmatischen Nutzung zur Verfügung.

Die Verpackungsoptionen umfassen:

* Verschlüsselungsoptionen (Audio, Video, teilweise Verschlüsselung).
* Lizenzserver-URL, die der Client als Basis-URL für alle an den Lizenzserver gesendeten Anforderungen verwendet
* Lizenzservertransportzertifikat
* Lizenzserverzertifikat zum Verschlüsseln des CEK
* Packager-Berechtigung zum Signieren von Metadaten

