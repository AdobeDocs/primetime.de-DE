---
seo-title: Einbetten von Lizenzen
title: Einbetten von Lizenzen
uuid: e3d55376-07de-479c-9a53-04bc8071ced4
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Einbetten von Lizenzen {#embedding-licenses}

Sobald der Inhalt verschlüsselt wurde und eine Lizenz vorgeneriert wurde, kann die Lizenz in den verschlüsselten Inhalt eingebettet werden.

Wenn Sie eine Lizenz einbetten möchten, benötigen Sie eine Instanz von `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; Verwenden Sie andernfalls `MediaProcessorFactory.getMediaProcessor()`, um eine Instanz basierend auf dem erkannten Dateityp zurückzugeben. Anschließend müssen Sie ein `KeyMetaDataCallback` erstellen und `modifyKeyMetaData()` aufrufen. Ihre Callback-Implementierung wird dann aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Basierend auf den gefundenen Metadaten können Sie eine einzubettende Lizenz auswählen und die Lizenz mit `EmbedLicenseKeyMetaData.setEmbeddedLicenses()` festlegen.

Siehe `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` im Ordner &quot;Reference Implementation Command Line Tools [!DNL Samples]&quot;für Beispielcode, der eingebettete Lizenzen demonstriert.

>[!NOTE]
>
>Ein Adobe Primetime DRM 2.0-Client ignoriert alle Lizenzen, die in den Inhalt eingebettet sind, und versucht dann, eine Lizenz vom Lizenzserver zu erhalten, der in den Metadaten angegeben ist. Wenn die Metadaten jedoch darauf hindeuten, dass kein Lizenzserver verfügbar ist, muss ein Primetime-DRM 2.0-Client aktualisiert werden, bevor Sie den Inhalt Ansicht haben.

