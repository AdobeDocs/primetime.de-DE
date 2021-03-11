---
title: Einbetten von Lizenzen
description: Einbetten von Lizenzen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Einbetten von Lizenzen {#embedding-licenses}

Sobald der Inhalt verschlüsselt wurde und eine Lizenz vorgeneriert wurde, kann die Lizenz in den verschlüsselten Inhalt eingebettet werden.

Um eine Lizenz einzubetten, rufen Sie eine Instanz von `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater` ab. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; Verwenden Sie andernfalls `MediaProcessorFactory.getMediaProcessor()`, um eine Instanz basierend auf dem erkannten Dateityp zurückzugeben. Erstellen Sie ein `KeyMetaDataCallback` und rufen Sie `modifyKeyMetaData()` auf. Ihre Callback-Implementierung wird aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Basierend auf den gefundenen Metadaten können Sie eine einzubettende Lizenz auswählen und die Lizenz mit `EmbedLicenseKeyMetaData.setEmbeddedLicenses()` festlegen.

Beispiel-Code, der eingebettete Lizenzen demonstriert, finden Sie unter `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` im Verzeichnis der Implementierungs-Befehlszeilenwerkzeuge &quot;Beispiele&quot;.

>[!NOTE]
>
>Adobe Access 2.0-Clients ignorieren alle im Inhalt eingebetteten Lizenzen und versuchen, eine Lizenz vom in den Metadaten angegebenen Lizenzserver zu erhalten. Wenn die Metadaten jedoch darauf hindeuten, dass kein Lizenzserver verfügbar ist, muss ein Adobe Access 2.0-Client auf die Ansicht des Inhalts aktualisieren.

Siehe [Out-of-Band-Lizenzen](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
