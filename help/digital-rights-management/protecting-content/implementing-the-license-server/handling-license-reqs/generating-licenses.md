---
seo-title: Generieren von Lizenzen
title: Generieren von Lizenzen
uuid: f91b0cc8-e0ed-4722-947b-22eb2bfba916
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Generieren von Lizenzen{#generating-licenses}

Wenn Sie einem Benutzer eine Blattlizenz ausstellen möchten, muss das SDK das in den Inhaltsmetadaten enthaltene CEK entschlüsseln und es für den Computer, der eine Lizenz anfordert, erneut verschlüsseln. Zum Entschlüsseln des CEK muss der Server die zum Entschlüsseln des Schlüssels erforderlichen Informationen bereitstellen. Rufen Sie `ContentInfo.setKeyRetrievalInfo()` auf und geben Sie ein `AsymmetricKeyRetrieval`-Objekt ein. Wenn die Metadaten mehrere Richtlinien enthalten, muss der Server festlegen, welche Richtlinie verwendet werden soll, und `LicenseRequestMessage.setSelectedPolicy()` aufrufen. Rufen Sie dann `LicenseRequestMessage.generateLicense()` auf, um die Lizenz zu generieren. Mit dem zurückgegebenen `License`-Objekt können Sie den Ablauf oder die Rechte in der Lizenz ändern.

Wenn im `ContentInfo`-Objekt ein `ExternalKeyRetrieval`-Objekt angegeben ist, wird erwartet, dass der Lizenzserver die zugehörige CEK-ID verwendet, um das entsprechende CEK abzurufen, das in die Lizenz eingefügt wurde.

Weitere Informationen zur Verwendung des Arbeitsablaufs für externe CEK finden Sie unter [Adobe Primetime DRM External CEK Overview](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).
