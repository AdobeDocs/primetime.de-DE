---
title: Untersuchen von verschlüsselten Dateiinhalten
description: Untersuchen von verschlüsselten Dateiinhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Untersuchen von verschlüsselten Dateiinhalten {#examining-encrypted-file-content}

So prüfen Sie den Inhalt einer FLV- oder F4V-Datei mithilfe der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter [Einrichten der Development-Umgebung](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `MediaEncrypter`-Instanz.
1. Übergeben Sie die verschlüsselte Datei an die `MediaEncrypter.examineEncryptedContent`-Methode, die ein `KeyMetaData`-Objekt zurückgibt.
1. Inspect Sie die Informationen im `KeyMetaData`-Objekt.

Beispielcode zum Extrahieren von DRM-Metadaten aus einer verschlüsselten Datei finden Sie unter `com.adobe.flashaccess.samples.mediapackager.ExamineContent` im Ordner &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
