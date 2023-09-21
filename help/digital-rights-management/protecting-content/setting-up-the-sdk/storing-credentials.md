---
title: Speichern von Anmeldeinformationen
description: Speichern von Anmeldeinformationen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Speichern von Anmeldeinformationen{#storing-credentials}

Das Primetime DRM SDK unterstützt verschiedene Methoden zum Speichern von Anmeldeinformationen, einschließlich der Verwendung eines Hardware Security Module (HSM) oder einer PKCS12-Datei. Das SDK verwendet eine Berechtigung (Zertifikat mit öffentlichem Schlüssel und zugehörigen privaten Schlüssel), wenn der private Schlüssel erforderlich ist. Beispielsweise verwendet der Packager eine Berechtigung zum Signieren von Metadaten. Der Lizenzserver verwendet eine Berechtigung zum Entschlüsseln von Daten, die mit dem Lizenzserver oder öffentlichen Transportschlüssel verschlüsselt wurden.

Sie müssen private Schlüssel sorgfältig schützen, um die Sicherheit Ihres Inhalts und Lizenzservers zu gewährleisten. PKCS12 ist ein Standard-Archivdateiformat zum Speichern von mit einem Kennwort verschlüsselten Anmeldeinformationen. (Sie können die PKCS12-Datei auch selbst verschlüsseln und signieren.) Die Dateierweiterung [!DNL .pfx] wird häufig für Dateien verwendet, die dieses Format unterstützen.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines HSM für maximale Sicherheit.
>
>Siehe *Richtlinien zur sicheren Bereitstellung von Adobe Primetime DRM* Handbuch.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java 64-Bit für Windows nicht mehr die PKCS11-Schnittstellen, die Primetime DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, müssen Sie eine 32-Bit-Version von Java verwenden oder ein JDK verwenden, das die vollständigen PKCS11-Schnittstellen unterstützt.

Sie können einen privaten Schlüssel in einem HSM-System speichern und das Primetime DRM SDK verwenden, um die Berechtigung, die Sie vom HSM erhalten, zu übergeben. Wenn Sie eine Berechtigung verwenden möchten, die in einem HSM gespeichert ist, müssen Sie einen JCE-Provider verwenden, der mit einem HSM kommunizieren kann, um einen Handle für den privaten Schlüssel zu erhalten. Dann müssen Sie den Handle, den Namen des privaten Schlüssels und das Zertifikat, das den öffentlichen Schlüssel enthält, an `ServerCredentialFactory.getServerCredential()`.

Der SunPKCS11-Provider stellt ein Beispiel für einen JCE-Provider dar, mit dem Sie auf einen privaten Schlüssel in einem HSM zugreifen können. Einige HSMs sind auch mit einem Java-SDK enthalten, das mit einem JCE-Provider gebündelt wird.

Anweisungen zur Verwendung dieses Providers finden Sie in der Sun Java-Dokumentation .

PEM und DER sind Methoden zum Kodieren eines Zertifikats mit öffentlichem Schlüssel. PEM ist eine Base-64-Kodierung und DER ist eine binäre Kodierung. Zertifikatdateien verwenden normalerweise die Erweiterung [!DNL .cer], [!DNL .pem]oder [!DNL .der]. Zertifikate werden verwendet, wenn nur ein öffentlicher Schlüssel erforderlich ist. Wenn für eine Komponente nur der öffentliche Schlüssel verwendet werden muss, wird empfohlen, dass Sie diese Komponente mit dem Zertifikat anstelle einer Berechtigung oder PKCS12-Datei bereitstellen.
