---
title: Überprüfen verschlüsselter Dateiinhalte
description: Überprüfen verschlüsselter Dateiinhalte
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Überprüfen verschlüsselter Dateiinhalte{#examining-encrypted-file-content}

Sie können den Inhalt einer verschlüsselten Mediendatei mithilfe der Java-API überprüfen.

Überprüfen des verschlüsselten Dateiinhalts:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein. Siehe *Einrichten des SDK* für Ihr Projekt.
1. Erstellen Sie eine `MediaEncrypter` -Instanz.
1. Übergeben Sie die verschlüsselte Datei an die `MediaEncrypter.examineEncryptedContent` -Methode, die eine `KeyMetaData` -Objekt.

1. Inspect die Informationen in der `KeyMetaData` -Objekt.

Beispielcode, der beschreibt, wie DRM-Metadaten aus einer verschlüsselten Datei extrahiert werden, finden Sie unter `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in den Befehlszeilenwerkzeugen für die Referenzimplementierung [!DNL samples/] Verzeichnis.
