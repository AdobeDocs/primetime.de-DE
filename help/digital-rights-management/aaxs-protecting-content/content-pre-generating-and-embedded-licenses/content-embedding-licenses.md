---
seo-title: Einbetten von Lizenzen
title: Einbetten von Lizenzen
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Einbetten von Lizenzen {#embedding-licenses}

Sobald der Inhalt verschlüsselt wurde und eine Lizenz vorgeneriert wurde, kann die Lizenz in den verschlüsselten Inhalt eingebettet werden.

Um eine Lizenz einzubetten, rufen Sie eine Instanz von `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`ab. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; Andernfalls können Sie eine Instanz `MediaProcessorFactory.getMediaProcessor()` basierend auf dem erkannten Dateityp zurückgeben. Erstellen Sie eine `KeyMetaDataCallback` und rufen Sie auf `modifyKeyMetaData()`. Ihre Callback-Implementierung wird aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Anhand der gefundenen Metadaten können Sie eine Lizenz zum Einbetten auswählen und die Lizenz mit `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`festlegen.

Beispiel-Code, der eingebettete Lizenzen demonstriert, finden Sie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` im Verzeichnis &quot;Beispiele&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Adobe Access 2.0-Clients ignorieren alle im Inhalt eingebetteten Lizenzen und versuchen, eine Lizenz vom in den Metadaten angegebenen Lizenzserver zu erhalten. Wenn die Metadaten jedoch darauf hindeuten, dass kein Lizenzserver verfügbar ist, muss ein Adobe Access 2.0-Client auf die Ansicht des Inhalts aktualisieren.

Siehe [Out-of-Band-Lizenzen](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
