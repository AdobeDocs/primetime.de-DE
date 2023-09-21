---
title: Verschlüsseln von Inhalten
description: Verschlüsseln von Inhalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Verschlüsseln von Inhalten{#encrypting-content}

Zum Verschlüsseln von FLV- und F4V-Inhalten wird ein `MediaEncrypter` -Objekt. Sie können auch FLV- und F4V-Dateien verpacken, die nur Audiospuren enthalten. Beim Verschlüsseln von H.264-Inhalten für Geräte mit untergeordnetem Ausgang kann es praktisch sein, nur eine partielle Verschlüsselung anzuwenden, um die Leistung zu verbessern. In solchen Fällen kann eine F4V-Datei teilweise mit dem `F4VDRMParameters.setVideoEncryptionLevel`-Methode.

So verschlüsseln Sie eine FLV- oder F4V-Datei mit der Java-API:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die unter Einrichten der Entwicklungsumgebung in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredential` -Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `MediaEncrypter` -Instanz. Verwenden Sie eine `MediaEncryperFactory` wenn Sie nicht wissen, welche Art von Datei Sie haben. Andernfalls können Sie eine `FLVEncrypter` oder `F4VEncrypter` direkt.
1. Geben Sie die Verschlüsselungsoptionen mithilfe eines `DRMParameters` -Objekt.
1. Festlegen der Signaturoptionen mithilfe einer `SignatureParameters` -Objekt und übergeben Sie die `ServerCredential` Instanz auf ihre `setServerCredentials` -Methode.
1. Legen Sie Schlüssel und Lizenzinformationen mithilfe eines `V2KeyParameters` -Objekt. Legen Sie die Richtlinien mithilfe der `setPolicies` -Methode. Stellen Sie die Informationen ein, die der Client benötigt, um den Lizenzserver zu kontaktieren, indem Sie die `setLicenseServerUrl` und `setLicenseServerTransportCertificate` -Methoden. Legen Sie die CEK-Verschlüsselungsoptionen mithilfe der `setKeyProtectionOptions` -Methode und ihren benutzerdefinierten Eigenschaften mithilfe der `setCustomProperties` -Methode. Je nach verwendetem Verschlüsselungstyp können Sie abschließend die `DRMKeyParameters` -Objekt zu einem von `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`oder `F4VDRMParameters`und legen Sie die Verschlüsselungsoptionen fest.
1. Verschlüsseln Sie den Inhalt, indem Sie die Eingabe- und Ausgabedateien und Verschlüsselungsoptionen an die `MediaEncrypter.encryptContent` -Methode.

Beispielcode zum Verschlüsseln von Inhalten finden Sie unter `com.adobe.flashaccess.samples.mediapackager.EncryptContent` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
