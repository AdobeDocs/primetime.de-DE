---
seo-title: Verschlüsseln von Inhalten
title: Verschlüsseln von Inhalten
uuid: 03f33473-bcd4-4e06-a823-e944897cb28e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verschlüsseln von Inhalten{#encrypting-content}

Sie verschlüsseln Videoinhalte mit dem `MediaEncrypter` Objekt. Sie können Mediendateien verschlüsseln, die nur Audiospuren enthalten. Sie können auch nur eine partielle Verschlüsselung anwenden. zum Beispiel zur Verbesserung der Leistung bei der Verschlüsselung von H.264-Inhalten für Geräte mit niedrigem Ende.

So verschlüsseln Sie Mediendateien mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung ** in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredential` Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `MediaEncrypter` Instanz. Verwenden Sie eine Datei, `MediaEncryperFactory` wenn Sie nicht wissen, welche Art von Datei Sie haben.

1. Legen Sie die Verschlüsselungsoptionen mithilfe eines `DRMParameters` Objekts fest.
1. Legen Sie die Unterschriftsoptionen mit einem `SignatureParameters` Objekt fest und übergeben Sie die `ServerCredential` Instanz an ihre `setServerCredentials` Methode.

1. Legen Sie die Schlüssel- und Lizenzinformationen mithilfe eines `V2KeyParameters` Objekts fest. Legen Sie die DRM-Richtlinien mit der `setPolicies` Methode fest. Stellen Sie die vom Client benötigten Informationen ein, um den Lizenzserver zu kontaktieren, indem Sie die `setLicenseServerUrl` und- `setLicenseServerTransportCertificate` Methoden aufrufen. Legen Sie die CEK-Verschlüsselungsoptionen mit der `setKeyProtectionOptions` Methode und die benutzerdefinierten Eigenschaften mit der `setCustomProperties` Methode fest. Je nach verwendetem Verschlüsselungstyp können Sie das `DRMKeyParameters` Objekt schließlich in den entsprechenden Typ ( `VideoDRMParameters`, `AudioDRMParameters`) umwandeln und die Verschlüsselungsoptionen festlegen.

1. Verschlüsseln Sie den Inhalt, indem Sie die Eingabe- und Ausgabedateien und Verschlüsselungsoptionen an die `MediaEncrypter.encryptContent` Methode übergeben.

Beispielcode zum Verschlüsseln von Inhalten finden Sie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` im [!DNL samples/] Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge.
