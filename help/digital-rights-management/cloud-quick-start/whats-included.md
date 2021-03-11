---
description: Adobe bietet Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM License Server entwickeln und verwalten möchten, einen Cloud DRM-Dienst an. Durch die Nutzung dieses Service können Kunden die Betriebs- und Entwicklungskomplexität bei der Ausgabe von DRM-Lizenzen reduzieren. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Dieser DRM-Dienst wird von der Adobe gehostet und gewartet, mit einer Laufzeit von 24 Stunden.
title: Hintergrund
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Hintergrund {#background}

Adobe bietet Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM License Server entwickeln und verwalten möchten, einen Cloud DRM-Dienst an. Durch die Nutzung dieses Service können Kunden die Betriebs- und Entwicklungskomplexität bei der Ausgabe von DRM-Lizenzen reduzieren. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Dieser DRM-Dienst wird von der Adobe gehostet und gewartet, mit einer Laufzeit von 24 Stunden.

>[!NOTE]
>
>Adobe Primetime DRM hieß früher Adobe Access und davor Flash Access.

## Inhalt von Primetime Cloud DRM {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Benutzerdefiniertes Authentifizierungs-/Berechtigungsmodul und Anweisungen zum Einsatz der benutzerdefinierten Authentifizierung für Ihren Inhalt. Weitere Dokumentation finden Sie im Ordner [!DNL Custom Authentication Entitlement].
* Cloud DRM-spezifisches Lizenzserverzertifikat ( [!DNL .pem/.cer/.der])

* Cloud DRM-spezifisches Lizenzserver-Transportzertifikat ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Beispiel-DRM-Richtlinien für Verpackungen

   * **policy_24hr** - Lizenzcache auf Datenträger für 24 Stunden. Nach 24 Stunden muss eine neue Lizenz für die Ansicht des Inhalts erworben werden. Alle anderen Richtlinien in diesem Kit haben auch 24 Stunden Lizenz-Cache.
   * **policy_ios_remotekeyserver**  - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Zusätzlich erwirbt der Client alle AES-Entschlüsselungsschlüssel aus Cloud DRM. Die Wiedergabe auf iOS-Geräten mit intaktem Zugriff ist nicht zulässig.

   * **policy_ios_localkeyserver**  - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Zusätzlich erwirbt der Client alle HLS AES-Entschlüsselungsschlüssel von einem lokalen HTTP-Server anstelle von Cloud DRM. Die Wiedergabe auf iOS-Geräten mit intaktem Zugriff ist nicht zulässig.

   * **policy_adobePass**  - Der Client muss sich zunächst mit authentifizieren (früher Adobe Pass genannt), andernfalls wird eine Lizenz verweigert.

* Adobe Policy Manager-Tool zum Erstellen zusätzlicher DRM-Richtlinien
* Beispielvideoinhalt zum Verpacken

