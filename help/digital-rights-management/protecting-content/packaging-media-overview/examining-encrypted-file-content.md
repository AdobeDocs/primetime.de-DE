---
seo-title: Untersuchen von verschlüsselten Dateiinhalten
title: Untersuchen von verschlüsselten Dateiinhalten
uuid: 1b3318f6-0850-43f2-9127-c72ea81a1bdf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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
