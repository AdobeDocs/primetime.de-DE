---
title: Verschlüsseln von Inhalten
description: Verschlüsseln von Inhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Verschlüsseln von Inhalten{#encrypting-content}

Zum Verschlüsseln von FLV- und F4V-Inhalten wird ein `MediaEncrypter`-Objekt verwendet. Sie können auch FLV- und F4V-Dateien verpacken, die nur Audiospuren enthalten. Beim Verschlüsseln von H.264-Inhalten für Geräte mit niedrigem Ende ist es möglicherweise sinnvoll, nur eine partielle Verschlüsselung anzuwenden, um die Leistung zu verbessern. In solchen Fällen kann eine F4V-Datei mit der `F4VDRMParameters.setVideoEncryptionLevel`Methode teilweise verschlüsselt werden.

So verschlüsseln Sie eine FLV- oder F4V-Datei mit der Java-API:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredential`-Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `MediaEncrypter`-Instanz. Verwenden Sie einen `MediaEncryperFactory`, wenn Sie nicht wissen, welche Art von Datei Sie haben. Andernfalls können Sie direkt ein `FLVEncrypter` oder `F4VEncrypter` erstellen.
1. Legen Sie die Verschlüsselungsoptionen mit einem `DRMParameters`-Objekt fest.
1. Legen Sie die Unterschriftsoptionen mit einem `SignatureParameters`-Objekt fest und übergeben Sie die `ServerCredential`-Instanz an die `setServerCredentials`-Methode.
1. Legen Sie die Schlüssel- und Lizenzinformationen mit einem `V2KeyParameters`-Objekt fest. Legen Sie die Richtlinien mit der `setPolicies`-Methode fest. Stellen Sie die vom Client benötigten Informationen ein, um den Lizenzserver zu kontaktieren, indem Sie die Methoden `setLicenseServerUrl` und `setLicenseServerTransportCertificate` aufrufen. Legen Sie die CEK-Verschlüsselungsoptionen mit der `setKeyProtectionOptions`-Methode und ihren benutzerdefinierten Eigenschaften mit der `setCustomProperties`-Methode fest. Je nach verwendetem Verschlüsselungstyp können Sie schließlich das `DRMKeyParameters`-Objekt in eines von `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters` oder `F4VDRMParameters` umwandeln und die Verschlüsselungsoptionen festlegen.
1. Verschlüsseln Sie den Inhalt, indem Sie die Eingabe- und Ausgabedateien und Verschlüsselungsoptionen an die `MediaEncrypter.encryptContent`-Methode übergeben.

Beispielcode zum Verschlüsseln von Inhalten finden Sie unter `com.adobe.flashaccess.samples.mediapackager.EncryptContent` im Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge &quot;samples&quot;.
