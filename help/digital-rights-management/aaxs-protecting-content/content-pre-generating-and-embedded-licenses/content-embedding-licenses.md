---
title: Einbetten von Lizenzen
description: Einbetten von Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Einbetten von Lizenzen {#embedding-licenses}

Sobald der Inhalt verschlüsselt und eine Lizenz vorgeneriert wurde, kann die Lizenz in den verschlüsselten Inhalt eingebettet werden.

Um eine Lizenz einzubetten, rufen Sie eine Instanz von `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Wenn Sie den Typ des verschlüsselten Inhalts kennen, verwenden Sie den Konstruktor für `FLVKeyMetaDataUpdater` oder `F4VKeyMetaDataUpdater`; andernfalls verwenden Sie `MediaProcessorFactory.getMediaProcessor()` , um eine Instanz basierend auf dem erkannten Dateityp zurückzugeben. Erstellen Sie eine `KeyMetaDataCallback` und aufrufen `modifyKeyMetaData()`. Ihre Callback-Implementierung wird aufgerufen, wenn sich die DRM-Metadaten im verschlüsselten Inhalt befinden. Basierend auf den gefundenen Metadaten können Sie eine Lizenz auswählen, die eingebettet werden soll, und die Lizenz mithilfe von `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Beispielcode für eingebettete Lizenzen finden Sie unter `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` im Verzeichnis &quot;Beispiele&quot;der Befehlszeilenwerkzeuge für die Referenzimplementierung.

>[!NOTE]
>
>Adobe Access 2.0-Clients ignorieren alle im Inhalt eingebetteten Lizenzen und versuchen, eine Lizenz vom Lizenzserver zu erhalten, der in den Metadaten angegeben ist. Wenn die Metadaten jedoch darauf hinweisen, dass kein Lizenzserver verfügbar ist, muss ein Adobe Access 2.0-Client aktualisiert werden, um den Inhalt anzuzeigen.

Siehe [Out-of-Band-Lizenzen](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
