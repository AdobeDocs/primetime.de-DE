---
title: Lizenzen erstellen
description: Lizenzen erstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Lizenzen erstellen {#generating-licenses}

Um dem Benutzer eine Laublizenz zu erteilen, muss das SDK das in den Inhaltsmetadaten enthaltene CEK entschlüsseln und für den Computer, der eine Lizenz anfordert, erneut verschlüsseln. Zum Entschlüsseln des CEK muss der Server die zum Entschlüsseln des Schlüssels erforderlichen Informationen bereitstellen. Aufruf `ContentInfo.setKeyRetrievalInfo()` und stellen `AsymmetricKeyRetrieval` -Objekt. Wenn die Metadaten mehrere Richtlinien enthalten, muss der Server festlegen, welche Richtlinie verwendet werden soll, und aufrufen `LicenseRequestMessage.setSelectedPolicy()`. Dann aufrufen `LicenseRequestMessage.generateLicense()` um die Lizenz zu generieren. Verwenden der `License` -Objekt, das zurückgegeben wird, können Sie die Gültigkeit oder Rechte in der Lizenz ändern.

Wenn ein ExternalKeyRetrieval -Objekt im `ContentInfo` -Objekt verwenden, wird erwartet, dass der Lizenzserver die zugehörige CEK-ID verwendet, um das entsprechende CEK abzurufen, das in die Lizenz eingefügt wird. Weitere Informationen zur Verwendung des externen CEK-Workflows finden Sie unter [Adobe Access DRM External CEK - Überblick](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
