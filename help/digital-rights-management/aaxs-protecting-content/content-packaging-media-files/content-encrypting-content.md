---
seo-title: Verschlüsseln von Inhalten
title: Verschlüsseln von Inhalten
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verschlüsseln von Inhalten{#encrypting-content}

Beim Verschlüsseln von FLV- und F4V-Inhalten wird ein `MediaEncrypter` Objekt verwendet. Sie können auch FLV- und F4V-Dateien verpacken, die nur Audiospuren enthalten. Beim Verschlüsseln von H.264-Inhalten für Geräte mit niedrigem Ende ist es möglicherweise sinnvoll, nur eine partielle Verschlüsselung anzuwenden, um die Leistung zu verbessern. In solchen Fällen kann eine F4V-Datei mit der `F4VDRMParameters.setVideoEncryptionLevel`Methode teilweise verschlüsselt werden.

So verschlüsseln Sie eine FLV- oder F4V-Datei mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredential` Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `MediaEncrypter` Instanz. Verwenden Sie eine Datei, `MediaEncryperFactory` wenn Sie nicht wissen, welche Art von Datei Sie haben. Andernfalls können Sie eine `FLVEncrypter` oder `F4VEncrypter` direkt erstellen.
1. Legen Sie die Verschlüsselungsoptionen mithilfe eines `DRMParameters` Objekts fest.
1. Legen Sie die Unterschriftsoptionen mit einem `SignatureParameters` Objekt fest und übergeben Sie die `ServerCredential` Instanz an ihre `setServerCredentials` Methode.
1. Legen Sie die Schlüssel- und Lizenzinformationen mithilfe eines `V2KeyParameters` Objekts fest. Legen Sie die Richtlinien mit der `setPolicies` Methode fest. Stellen Sie die vom Client benötigten Informationen ein, um den Lizenzserver zu kontaktieren, indem Sie die `setLicenseServerUrl` und- `setLicenseServerTransportCertificate` Methoden aufrufen. Legen Sie die CEK-Verschlüsselungsoptionen mit der `setKeyProtectionOptions` Methode und die benutzerdefinierten Eigenschaften mit der `setCustomProperties` Methode fest. Je nach verwendetem Verschlüsselungstyp können Sie das `DRMKeyParameters` Objekt schließlich in eine der Optionen `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`oder `F4VDRMParameters`umwandeln und die Verschlüsselungsoptionen festlegen.
1. Verschlüsseln Sie den Inhalt, indem Sie die Eingabe- und Ausgabedateien und Verschlüsselungsoptionen an die `MediaEncrypter.encryptContent` Methode übergeben.

Beispiel-Code zum Verschlüsseln von Inhalten finden Sie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
