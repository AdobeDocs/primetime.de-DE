---
title: Verschlüsseln von Inhalten
description: Verschlüsseln von Inhalten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Verschlüsseln von Inhalten{#encrypting-content}

Sie verschlüsseln Videoinhalte mit dem `MediaEncrypter` -Objekt. Sie können Mediendateien verschlüsseln, die nur Audiospuren enthalten. Sie können auch nur eine partielle Verschlüsselung anwenden, z. B. um die Leistung beim Verschlüsseln von H.264-Inhalten für Geräte im unteren Bereich zu verbessern.

Verschlüsseln von Mediendateien mit der Java-API:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die in *Einrichten der Entwicklungsumgebung* in Ihrem Projekt.
1. Erstellen Sie eine `ServerCredential` -Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `MediaEncrypter` -Instanz. Verwenden Sie eine `MediaEncryperFactory` wenn Sie nicht wissen, welche Art von Datei Sie haben.

1. Geben Sie die Verschlüsselungsoptionen mithilfe eines `DRMParameters` -Objekt.
1. Festlegen der Signaturoptionen mithilfe einer `SignatureParameters` -Objekt und übergeben Sie die `ServerCredential` Instanz auf ihre `setServerCredentials` -Methode.

1. Legen Sie Schlüssel und Lizenzinformationen mithilfe eines `V2KeyParameters` -Objekt. Richten Sie die DRM-Richtlinien mithilfe des `setPolicies` -Methode. Stellen Sie die Informationen ein, die der Client benötigt, um den Lizenzserver zu kontaktieren, indem Sie die `setLicenseServerUrl` und `setLicenseServerTransportCertificate` -Methoden. Legen Sie die CEK-Verschlüsselungsoptionen mithilfe der `setKeyProtectionOptions` -Methode und ihren benutzerdefinierten Eigenschaften mithilfe der `setCustomProperties` -Methode. Je nach verwendetem Verschlüsselungstyp können Sie abschließend die `DRMKeyParameters` Objekt auf den entsprechenden Typ ( `VideoDRMParameters`, `AudioDRMParameters`) und legen Sie die Verschlüsselungsoptionen fest.

1. Verschlüsseln Sie den Inhalt, indem Sie die Eingabe- und Ausgabedateien und Verschlüsselungsoptionen an die `MediaEncrypter.encryptContent` -Methode.

Beispielcode, der zeigt, wie Inhalte verschlüsselt werden, finden Sie unter `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in den Befehlszeilenwerkzeugen für die Referenzimplementierung [!DNL samples/] Verzeichnis.
