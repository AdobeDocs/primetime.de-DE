---
seo-title: Embedding licenses
title: Embedding licenses
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Embedding licenses {#embedding-licenses}

Once content has been encrypted and a license has been pre-generated, the license may be embedded into the encrypted content.

To embed a license, obtain an instance of `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; Andernfalls können Sie eine Instanz `MediaProcessorFactory.getMediaProcessor()` basierend auf dem erkannten Dateityp zurückgeben. Erstellen Sie eine `KeyMetaDataCallback` und rufen Sie auf `modifyKeyMetaData()`. Ihre Callback-Implementierung wird aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Based on the metadata found, you can choose a license to embed and set the license using `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

For sample code demonstrating embedded licenses, see `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in the Reference Implementation Command Line Tools “Samples” directory.

>[!NOTE]
>
>Adobe Access 2.0-Clients ignorieren alle im Inhalt eingebetteten Lizenzen und versuchen, eine Lizenz vom in den Metadaten angegebenen Lizenzserver zu erhalten. Wenn die Metadaten jedoch darauf hindeuten, dass kein Lizenzserver verfügbar ist, muss ein Adobe Access 2.0-Client auf die Ansicht des Inhalts aktualisieren.

Siehe [Out-of-Band-Lizenzen](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
