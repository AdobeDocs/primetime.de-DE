---
description: Wenn Sie ein HSM auswählen, um Ihre Serverberechtigungen zu speichern, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine Konfigurationsdatei "pkcs11.cfg"erstellen.
title: HSM-Konfiguration
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# HSM-Konfiguration{#hsm-configuration}

Wenn Sie ein HSM auswählen, um Ihre Serverberechtigungen zu speichern, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine Konfigurationsdatei &quot;pkcs11.cfg&quot;erstellen.

Sie müssen die Konfigurationsdatei im Ordner *LicenseServer.ConfigRoot* suchen.

Eine Beispielkonfigurationsdatei für PKCS11 finden Sie im Ordner [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] auf der Adobe Primetime DRM-DVD.

Informationen zum Format der Datei [!DNL pkcs11.cfg] finden Sie in der Sun PKCS11-Provider-Dokumentation.

Sie können den folgenden Befehl aus dem Ordner verwenden, in dem sich die Datei [!DNL pkcs11.cfg] befindet ( [!DNL keytool] wird mit Java JRE und JDK installiert), um zu überprüfen, ob die Konfigurationsdatei für HSM und Sun PKCS11 korrekt konfiguriert wurde:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Sie Ihre Anmeldeinformationen in der Liste Ansicht haben, ist das HSM korrekt konfiguriert und der Lizenzserver kann nun auf die Anmeldeinformationen zugreifen.
