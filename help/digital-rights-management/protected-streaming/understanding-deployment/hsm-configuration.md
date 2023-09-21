---
description: Wenn Sie ein HSM auswählen, um Ihre Serverberechtigungen zu speichern, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine Konfigurationsdatei pkcs11.cfg erstellen.
title: HSM-Konfiguration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# HSM-Konfiguration{#hsm-configuration}

Wenn Sie ein HSM auswählen, um Ihre Serverberechtigungen zu speichern, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine Konfigurationsdatei pkcs11.cfg erstellen.

Sie müssen die Konfigurationsdatei im *LicenseServer.ConfigRoot* Verzeichnis.

Siehe [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] -Verzeichnis auf der Adobe Primetime DRM DVD für eine Beispiel-PKCS1-Konfigurationsdatei.

Informationen zum Format von finden Sie in der Sun PKCS11-Provider-Dokumentation [!DNL pkcs11.cfg] -Datei.

Sie können den folgenden Befehl aus dem Verzeichnis verwenden, in dem die Variable [!DNL pkcs11.cfg] Datei befindet sich ( [!DNL keytool] mit Java JRE und JDK installiert ist), um zu überprüfen, ob die Konfigurationsdatei &quot;HSM&quot;und &quot;Sun PKCS11&quot;ordnungsgemäß konfiguriert wurde:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Sie Ihre Anmeldedaten in der Liste anzeigen können, ist das HSM korrekt konfiguriert und der Lizenzserver kann jetzt auf die Anmeldedaten zugreifen.
