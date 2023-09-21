---
description: Adobe bietet einen Cloud DRM-Dienst für Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM-Lizenzserver entwickeln und unterhalten möchten. Durch die Nutzung dieses Service können Kunden die betriebliche und entwicklungspolitische Komplexität im Zusammenhang mit der Ausstellung von DRM-Lizenzen verringern. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Dieser DRM-Dienst wird von Adobe gehostet und gepflegt, mit 24/7 Betriebszeit.
title: Hintergrund
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Hintergrund {#background}

Adobe bietet einen Cloud DRM-Dienst für Adobe Primetime DRM-Kunden, die keinen eigenen Primetime DRM-Lizenzserver entwickeln und unterhalten möchten. Durch die Nutzung dieses Service können Kunden die betriebliche und entwicklungspolitische Komplexität im Zusammenhang mit der Ausstellung von DRM-Lizenzen verringern. Primetime Cloud DRM kann DRM-Lizenzen für alle Geräte ausstellen, die eine Primetime Browser TVSDK-fähige Videoanwendung ausführen können, z. B. iOS, Android, Desktops und Xbox360. Dieser DRM-Dienst wird von Adobe gehostet und gepflegt, mit 24/7 Betriebszeit.

>[!NOTE]
>
>Adobe Primetime DRM hieß früher Adobe Access und davor Flash Access.

## Was ist in Primetime Cloud DRM enthalten? {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Benutzerdefiniertes Authentifizierungs-/Berechtigungsmodul und Anweisungen zum Aktivieren der benutzerdefinierten Authentifizierung für Ihren Inhalt. Weitere Informationen finden Sie im Abschnitt [!DNL Custom Authentication Entitlement] Verzeichnis.
* Cloud DRM-spezifisches Lizenzserver-Zertifikat ( [!DNL .pem/.cer/.der])

* Cloud DRM-spezifisches Lizenzserver-Transportzertifikat ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Beispiel-DRM-Richtlinien für das Verpacken

   * **policy_24hr** - Lizenziert den Cache auf dem Datenträger für 24 Stunden. Nach 24 Stunden muss eine neue Lizenz erworben werden, um den Inhalt anzeigen zu können. Alle anderen Richtlinien in diesem Kit verfügen auch über 24-Stunden-Lizenzzwischenspeicherung.
   * **policy_ios_remotekeyserver** - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Darüber hinaus bezieht der Client alle AES-Entschlüsselungsschlüssel von Cloud DRM. Die Wiedergabe ist auf inhaftierten iOS-Geräten nicht zulässig.

   * **policy_ios_localkeyserver** - Auf iOS-Geräten wird die DRM-Lizenz von Cloud DRM erworben. Darüber hinaus bezieht der Client alle HLS AES-Entschlüsselungsschlüssel von einem lokalen HTTP-Server anstelle von Cloud DRM. Die Wiedergabe ist auf inhaftierten iOS-Geräten nicht zulässig.

   * **policy_adobePass** - Der Client muss sich zunächst bei authentifizieren (früher Adobe Pass genannt) oder eine Lizenz wird verweigert.

* Adobe Policy Manager-Tool zum Erstellen zusätzlicher DRM-Richtlinien
* Beispielvideoinhalt für die Verpackung
