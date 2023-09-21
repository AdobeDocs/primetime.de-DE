---
title: Speichern von Anmeldeinformationen
description: Speichern von Anmeldeinformationen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Speichern von Anmeldeinformationen{#storing-credentials}

Das SDK unterstützt mehrere Methoden zum Speichern von Anmeldeinformationen (ein Zertifikat mit öffentlichem Schlüssel und der zugehörigen privaten Schlüssel) , einschließlich HSM oder PKCS12-Datei. Anmeldeinformationen werden verwendet, wenn der private Schlüssel erforderlich ist (z. B. für den Packager, um die Metadaten zu signieren, oder für das Entschlüsseln von Daten durch den Lizenzserver oder den öffentlichen Transportschlüssel). Private Schlüssel müssen sorgfältig überwacht werden, um die Sicherheit Ihres Inhalts und Lizenzservers zu gewährleisten. PKCS12 ist ein Standardformat für eine Datei, die eine mit einem Kennwort verschlüsselte Berechtigung enthält. Die Dateierweiterung .pfx wird häufig für Dateien dieses Formats verwendet.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines HSM für maximale Sicherheit. Weitere Informationen finden Sie in den Richtlinien für den Adobe-Zugriff auf sichere Bereitstellungen .

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64 Bit nicht die PKCS11-Schnittstellen, die Adobe Access DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, verwenden Sie bitte eine 32-Bit-Version von Java oder ein JDK, das die vollständigen PKCS11-Schnittstellen unterstützt.

Sie können einen privaten Schlüssel in einem Hardware-Sicherheitsmodul (HSM) belassen und das SDK verwenden, um die vom HSM abgerufenen Anmeldedaten zu übergeben. Um eine auf einem HSM gespeicherte Berechtigung zu verwenden, verwenden Sie einen JCE-Provider, der mit einem HSM kommunizieren kann, um einen Handle für den privaten Schlüssel zu erhalten. Übergeben Sie dann den Handle des privaten Schlüssels, den Namen des Anbieters und das Zertifikat mit dem öffentlichen Schlüssel an `ServerCredentialFactory.getServerCredential()`.

Der SunPKCS11-Provider ist ein Beispiel für einen JCE-Provider, der für den Zugriff auf einen privaten Schlüssel auf einem HSM verwendet werden kann (Anweisungen zur Verwendung dieses Providers finden Sie in der Sun Java-Dokumentation ). Einige HSMs enthalten auch ein Java-SDK, das einen JCE-Provider enthält.

PEM und DER bieten zwei Möglichkeiten, ein Zertifikat mit öffentlichem Schlüssel zu kodieren. PEM ist eine Base-64-Kodierung und DER ist eine binäre Kodierung. Zertifikatdateien verwenden normalerweise die Erweiterung .cer, .pem. oder .der. Zertifikate werden an Orten verwendet, an denen nur der öffentliche Schlüssel erforderlich ist. Wenn für eine Komponente nur der öffentliche Schlüssel verwendet werden muss, ist es besser, diese Komponente mit dem Zertifikat anstelle einer Berechtigung oder PKCS12-Datei bereitzustellen.
