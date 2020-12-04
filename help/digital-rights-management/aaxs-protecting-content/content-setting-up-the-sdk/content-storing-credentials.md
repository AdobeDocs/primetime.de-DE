---
seo-title: Speichern von Anmeldeinformationen
title: Speichern von Anmeldeinformationen
uuid: dbce523c-32d9-423f-bc95-39786f85fc29
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Speichern von Anmeldeinformationen{#storing-credentials}

Das SDK unterstützt mehrere Möglichkeiten zum Speichern von Berechtigungen (ein Zertifikat mit öffentlichem Schlüssel und der dazugehörige private Schlüssel), auch auf einem HSM oder als PKCS12-Datei. Anmeldeinformationen werden verwendet, wenn der private Schlüssel erforderlich ist (z. B. für das Signieren der Metadaten durch den Packager oder für das Entschlüsseln von mit dem Lizenzserver oder öffentlichen Transportschlüssel verschlüsselten Daten durch den License Server). Private Schlüssel müssen engmaschig überwacht werden, um die Sicherheit Ihres Inhalts und Lizenzservers zu gewährleisten. PKCS12 ist ein Standardformat für eine Datei, die eine mit einem Kennwort verschlüsselte Berechtigung enthält. Die Dateierweiterung .pfx wird häufig für Dateien dieses Formats verwendet.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung eines HSM für maximale Sicherheit. Weitere Informationen finden Sie unter Richtlinien für den Zugriff auf sichere Adoben.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64 Bit nicht die PKCS11-Schnittstellen, die Adobe Access DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, verwenden Sie bitte eine 32-Bit-Version von Java oder ein JDK, das die vollständigen PKCS11-Schnittstellen unterstützt.

Sie können einen privaten Schlüssel auf einem Hardware-Sicherheitsmodul (HSM) behalten und das SDK verwenden, um die Berechtigung, die Sie vom HSM erhalten, weiterzugeben. Um eine auf einem HSM gespeicherte Berechtigung zu verwenden, verwenden Sie einen JCE-Anbieter, der mit einem HSM kommunizieren kann, um einen Handle für den privaten Schlüssel zu erhalten. Übergeben Sie dann das Handle des privaten Schlüssels, den Namen des Anbieters und das Zertifikat mit dem öffentlichen Schlüssel an `ServerCredentialFactory.getServerCredential()`.

Der SunPKCS11-Anbieter ist ein Beispiel für einen JCE-Anbieter, der für den Zugriff auf einen privaten Schlüssel auf einem HSM verwendet werden kann (Anweisungen zur Verwendung dieses Providers finden Sie in der Sun Java-Dokumentation). Einige HSMs verfügen auch über ein Java SDK, das einen JCE-Anbieter enthält.

PEM und DER sind zwei Methoden zum Kodieren eines Zertifikats mit öffentlichem Schlüssel. PEM ist eine Base-64-Kodierung und DER ist eine binäre Kodierung. Zertifikatdateien verwenden in der Regel die Erweiterungen .cer, .pem. oder .der. Zertifikate werden an Orten verwendet, an denen nur der öffentliche Schlüssel erforderlich ist. Wenn eine Komponente nur den öffentlichen Schlüssel benötigt, um zu funktionieren, ist es besser, diese Komponente mit dem Zertifikat anstelle einer Berechtigung oder PKCS12-Datei bereitzustellen.
