---
description: Adobe bietet Adobe einen Cloud DRM-Dienst für Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM License Server entwickeln und verwalten möchten. Durch die Nutzung dieses Service können Kunden die Betriebs- und Entwicklungskomplexität bei der Ausgabe von DRM-Lizenzen reduzieren. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Der DRM-Dienst wird rund um die Uhr von Adobe gehostet und gewartet.
seo-description: Adobe bietet Adobe einen Cloud DRM-Dienst für Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM License Server entwickeln und verwalten möchten. Durch die Nutzung dieses Service können Kunden die Betriebs- und Entwicklungskomplexität bei der Ausgabe von DRM-Lizenzen reduzieren. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Der DRM-Dienst wird rund um die Uhr von Adobe gehostet und gewartet.
seo-title: Hintergrund
title: Hintergrund
uuid: 11a5b9ea-ebd2-47e0-b078-af2a3e1f7bf6
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Hintergrund {#background}

Adobe bietet Adobe einen Cloud DRM-Dienst für Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM License Server entwickeln und verwalten möchten. Durch die Nutzung dieses Service können Kunden die Betriebs- und Entwicklungskomplexität bei der Ausgabe von DRM-Lizenzen reduzieren. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Der DRM-Dienst wird rund um die Uhr von Adobe gehostet und gewartet.

>[!NOTE]
>
>Adobe Primetime DRM hieß früher Adobe Access und davor Flash Access.

## Im Lieferumfang von Primetime Cloud DRM enthalten {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Benutzerdefiniertes Authentifizierungs-/Berechtigungsmodul und Anweisungen zum Einsatz der benutzerdefinierten Authentifizierung für Ihren Inhalt. Weitere Dokumentation finden Sie im [!DNL Custom Authentication Entitlement] Verzeichnis.
* Cloud DRM-spezifisches Lizenzserverzertifikat ( [!DNL .pem/.cer/.der])

* Cloud DRM-spezifisches Lizenzserver-Transportzertifikat ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Beispiel-DRM-Richtlinien für Verpackungen

   * **policy_24hr** - Lizenzcache auf Datenträger für 24 Stunden. Nach 24 Stunden muss eine neue Lizenz für die Ansicht des Inhalts erworben werden. Alle anderen Richtlinien in diesem Kit haben auch 24 Stunden Lizenz-Cache.
   * **policy_ios_remotekeyserver** - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Zusätzlich erwirbt der Client alle AES-Entschlüsselungsschlüssel aus Cloud DRM. Die Wiedergabe auf iOS-Geräten mit intaktem Zugriff ist nicht zulässig.

   * **policy_ios_localkeyserver** - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Zusätzlich erwirbt der Client alle HLS AES-Entschlüsselungsschlüssel von einem lokalen HTTP-Server anstelle von Cloud DRM. Die Wiedergabe auf iOS-Geräten mit intaktem Zugriff ist nicht zulässig.

   * **policy_adobePass** - Der Client muss sich zunächst mit authentifizieren (früher Adobe Pass genannt), andernfalls wird eine Lizenz verweigert.

* Adobe Policy Manager-Tool zum Erstellen zusätzlicher DRM-Richtlinien
* Beispielvideoinhalt zum Verpacken

