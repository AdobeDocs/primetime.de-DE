---
title: HSM-Konfiguration
description: HSM-Konfiguration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# HSM-Konfiguration {#hsm-configuration}

Wenn Sie zum Speichern Ihrer Serverberechtigungen ein HSM verwenden möchten, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine [!DNL pkcs11.cfg] Konfigurationsdatei. Diese Datei muss sich im *LicenseServer.ConfigRoot* Verzeichnis. Siehe [!DNL Adobe Access Server for Protected Streaming/configs] -Verzeichnis auf der Adobe Access DVD für eine PKCS11-Beispielkonfigurationsdatei. Informationen zum Format von [!DNL pkcs11.cfg], siehe die Dokumentation zum Sun PKCS11-Provider .

Um zu überprüfen, ob die Konfigurationsdatei für HSM und Sun PKCS11 ordnungsgemäß konfiguriert ist, können Sie den folgenden Befehl aus dem Ordner verwenden, in dem die [!DNL pkcs11.cfg] Datei befindet sich ( [!DNL keytool] wird mit Java JRE und JDK installiert):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldeinformationen in der Liste angezeigt werden, ist das HSM ordnungsgemäß konfiguriert und der Lizenzserver kann auf die Anmeldeinformationen zugreifen.

>[!NOTE]
>
>Adobe Access Server für geschütztes Streaming unterstützt derzeit keine HSMs unter 64-Bit-Windows-Betriebssystemen.
