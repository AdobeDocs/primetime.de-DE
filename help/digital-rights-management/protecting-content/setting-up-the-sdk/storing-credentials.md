---
seo-title: Speichern von Anmeldeinformationen
title: Speichern von Anmeldeinformationen
uuid: a9e9db72-c921-4c28-ad1d-3fd3c2283f14
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Speichern von Anmeldeinformationen{#storing-credentials}

Das Primetime-DRM-SDK unterstützt verschiedene Methoden zum Speichern von Anmeldeinformationen, einschließlich der Verwendung eines Hardware Security Module (HSM) oder als PKCS12-Datei. Das SDK verwendet eine Berechtigung (öffentliches Schlüsselzertifikat und dazugehöriger privater Schlüssel), wenn der private Schlüssel erforderlich ist. Beispielsweise verwendet der Packager eine Berechtigung zum Signieren von Metadaten; Der License Server verwendet eine Berechtigung zum Entschlüsseln von Daten, die mit dem License Server oder dem öffentlichen Transportschlüssel verschlüsselt wurden.

Sie müssen private Schlüssel sorgfältig überwachen, um die Sicherheit Ihres Inhalts und Lizenzservers zu gewährleisten. PKCS12 ist ein standardmäßiges Archivdateiformat zum Speichern von Anmeldeinformationen, die mit einem Kennwort verschlüsselt wurden. (Sie können die PKCS12-Datei auch selbst verschlüsseln und signieren.) Die Dateierweiterung [!DNL .pfx] wird häufig für Dateien verwendet, die dieses Format unterstützen.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines HSM für maximale Sicherheit.
>
>See the *Adobe Primetime DRM Secure Deployment Guidelines* guide.

>[!NOTE]
>
>As of Java 1.7, 64-bit Sun Java for Windows no longer supports the PKCS11 interfaces that Primetime DRM requires for communicatation with HSM devices. If you plan to use an HSM, you need to use a 32-bit version of Java, or use a JDK that supports the full PKCS11 interfaces.

You can keep a private key on an HSM, and use the Primetime DRM SDK to pass in the credential you obtain from the HSM. If you want to use a credential that is stored on an HSM, you need to use a JCE provider that can communicate with an HSM to get a handle to the private key. Then you need to pass the private key handle, provider name, and certificate that includes the public key to `ServerCredentialFactory.getServerCredential()`.

The SunPKCS11 provider represents one example of a JCE provider that you can use to access a private key on an HSM. Some HSMs are also included with a Java SDK that is bundled with a JCE provider.

See the Sun Java documentation for instructions on how to use this provider.

PEM und DER sind Methoden zum Kodieren eines Zertifikats mit öffentlichem Schlüssel. PEM is a base-64 encoding and DER is a binary encoding. Zertifikatdateien verwenden in der Regel die Erweiterung [!DNL .cer], [!DNL .pem]oder [!DNL .der]. Zertifikate werden verwendet, wenn nur ein öffentlicher Schlüssel erforderlich ist. Wenn für eine Komponente nur der öffentliche Schlüssel erforderlich ist, sollten Sie diese Komponente mit dem Zertifikat anstelle einer Berechtigung oder PKCS12-Datei bereitstellen.
