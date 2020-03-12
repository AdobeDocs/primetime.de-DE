---
seo-title: Untersuchen von verschlüsselten Dateiinhalten
title: Untersuchen von verschlüsselten Dateiinhalten
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Untersuchen von verschlüsselten Dateiinhalten {#examining-encrypted-file-content}

So prüfen Sie den Inhalt einer FLV- oder F4V-Datei mithilfe der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung [](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `MediaEncrypter` Instanz.
1. Übergeben Sie die verschlüsselte Datei an die `MediaEncrypter.examineEncryptedContent` Methode, die ein `KeyMetaData` Objekt zurückgibt.
1. Überprüfen Sie die Informationen innerhalb des `KeyMetaData` Objekts.

Beispielcode zum Extrahieren von DRM-Metadaten aus einer verschlüsselten Datei finden Sie `com.adobe.flashaccess.samples.mediapackager.ExamineContent` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
