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
>Siehe Handbuch *Adobe Primetime DRM Secure Deployment Guidelines*.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64-Bit nicht mehr die PKCS11-Schnittstellen, die Primetime DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, müssen Sie eine 32-Bit-Version von Java oder ein JDK verwenden, das die vollständigen PKCS11-Schnittstellen unterstützt.

Sie können einen privaten Schlüssel auf einem HSM belassen und das Primetime DRM SDK verwenden, um die Berechtigung, die Sie über das HSM erhalten, weiterzugeben. Wenn Sie eine auf einem HSM gespeicherte Berechtigung verwenden möchten, müssen Sie einen JCE-Anbieter verwenden, der mit einem HSM kommunizieren kann, um einen Handle an den privaten Schlüssel zu erhalten. Dann müssen Sie den privaten Schlüsselhandgriff, den Anbieternamen und das Zertifikat, das den öffentlichen Schlüssel enthält, an `ServerCredentialFactory.getServerCredential()` übergeben.

Der SunPKCS11-Anbieter stellt ein Beispiel für einen JCE-Anbieter dar, mit dem Sie auf einen privaten Schlüssel auf einem HSM zugreifen können. Einige HSMs sind auch mit einem Java-SDK enthalten, das zum Lieferumfang eines JCE-Anbieters gehört.

Anweisungen zur Verwendung dieses Providers finden Sie in der Sun Java-Dokumentation.

PEM und DER sind Methoden zum Kodieren eines Zertifikats mit öffentlichem Schlüssel. PEM ist eine Base-64-Kodierung und DER ist eine binäre Kodierung. Zertifikatdateien verwenden normalerweise die Erweiterungen [!DNL .cer], [!DNL .pem] oder [!DNL .der]. Zertifikate werden verwendet, wenn nur ein öffentlicher Schlüssel erforderlich ist. Wenn für eine Komponente nur der öffentliche Schlüssel erforderlich ist, sollten Sie diese Komponente mit dem Zertifikat anstelle einer Berechtigung oder PKCS12-Datei bereitstellen.
