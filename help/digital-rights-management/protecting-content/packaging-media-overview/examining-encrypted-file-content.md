---
title: Untersuchen von verschlüsselten Dateiinhalten
description: Untersuchen von verschlüsselten Dateiinhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Untersuchen von verschlüsselten Dateiinhalten{#examining-encrypted-file-content}

Sie können den Inhalt einer verschlüsselten Mediendatei mithilfe der Java-API überprüfen.

So untersuchen Sie verschlüsselten Dateiinhalt:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein. Siehe *Einrichten des SDK* für Ihr Projekt.
1. Erstellen Sie eine `MediaEncrypter`-Instanz.
1. Übergeben Sie die verschlüsselte Datei an die `MediaEncrypter.examineEncryptedContent`-Methode, die ein `KeyMetaData`-Objekt zurückgibt.

1. Inspect Sie die Informationen im `KeyMetaData`-Objekt.

Beispiel-Code, der beschreibt, wie DRM-Metadaten aus einer verschlüsselten Datei extrahiert werden, finden Sie unter `com.adobe.flashaccess.samples.mediapackager.ExamineContent` im Ordner [!DNL samples/] der Referenzimplementierungs-Befehlszeilenwerkzeuge.
