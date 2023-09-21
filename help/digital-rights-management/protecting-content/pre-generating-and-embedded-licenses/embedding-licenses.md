---
title: Einbetten von Lizenzen
description: Einbetten von Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Einbetten von Lizenzen {#embedding-licenses}

Sobald der Inhalt verschlüsselt und eine Lizenz vorgeneriert wurde, kann die Lizenz in den verschlüsselten Inhalt eingebettet werden.

Wenn Sie eine Lizenz einbetten möchten, müssen Sie eine Instanz von `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; andernfalls verwenden Sie `MediaProcessorFactory.getMediaProcessor()` , um eine Instanz basierend auf dem erkannten Dateityp zurückzugeben. Anschließend müssen Sie eine `KeyMetaDataCallback` und aufrufen `modifyKeyMetaData()`. Ihre Callback-Implementierung wird dann aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Basierend auf den gefundenen Metadaten können Sie eine Lizenz auswählen, die eingebettet werden soll, und die Lizenz mithilfe von `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Siehe `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in den Befehlszeilenwerkzeugen für die Referenzimplementierung [!DNL Samples] -Verzeichnis für Beispielcode, der eingebettete Lizenzen zeigt.

>[!NOTE]
>
>Ein Adobe Primetime DRM 2.0-Client ignoriert alle Lizenzen, die in den Inhalt eingebettet sind, und versucht dann, eine Lizenz vom Lizenzserver zu erhalten, der in den Metadaten angegeben ist. Wenn die Metadaten jedoch darauf hinweisen, dass kein Lizenzserver verfügbar ist, muss ein Primetime-DRM 2.0-Client aktualisiert werden, bevor Sie den Inhalt anzeigen können.
