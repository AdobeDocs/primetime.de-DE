---
seo-title: Generieren von Lizenzen
title: Generieren von Lizenzen
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Generieren von Lizenzen {#generating-licenses}

Um dem Benutzer eine Laublizenz zu erteilen, muss das SDK das in den Inhaltsmetadaten enthaltene CEK entschlüsseln und es für den Computer, der eine Lizenz anfordert, erneut verschlüsseln. Zum Entschlüsseln des CEK muss der Server die zum Entschlüsseln des Schlüssels erforderlichen Informationen bereitstellen. Aufruf `ContentInfo.setKeyRetrievalInfo()` und Bereitstellung eines `AsymmetricKeyRetrieval` Objekts Wenn die Metadaten mehrere Richtlinien enthalten, muss der Server festlegen, welche Richtlinie verwendet und aufgerufen werden soll `LicenseRequestMessage.setSelectedPolicy()`. Rufen Sie dann `LicenseRequestMessage.generateLicense()` zur Generierung der Lizenz auf. Mithilfe des zurückgegebenen `License` Objekts können Sie den Ablauf oder die Rechte in der Lizenz ändern.

Wenn im `ContentInfo` Objekt ein ExternalKeyRetrieval-Objekt angegeben ist, wird erwartet, dass der Lizenzserver die zugehörige CEK-ID verwendet, um das entsprechende CEK abzurufen, das in die Lizenz eingefügt wird. Weitere Informationen zur Verwendung des Arbeitsablaufs für externe CEK finden Sie unter Übersicht über [Adobe Access DRM External CEK](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
