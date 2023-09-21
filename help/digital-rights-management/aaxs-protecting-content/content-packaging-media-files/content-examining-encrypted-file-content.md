---
title: Überprüfen verschlüsselter Dateiinhalte
description: Überprüfen verschlüsselter Dateiinhalte
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Überprüfen verschlüsselter Dateiinhalte {#examining-encrypted-file-content}

Um den Inhalt einer FLV- oder F4V-Datei mithilfe der Java-API zu untersuchen, führen Sie die folgenden Schritte aus:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die in [Einrichten der Entwicklungsumgebung](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt.
1. Erstellen Sie eine `MediaEncrypter` -Instanz.
1. Übergeben Sie die verschlüsselte Datei an die `MediaEncrypter.examineEncryptedContent` -Methode, die eine `KeyMetaData` -Objekt.
1. Inspect die Informationen in der `KeyMetaData` -Objekt.

Beispielcode, der veranschaulicht, wie DRM-Metadaten aus einer verschlüsselten Datei extrahiert werden, finden Sie unter `com.adobe.flashaccess.samples.mediapackager.ExamineContent` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
