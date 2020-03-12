---
seo-title: HSM-Konfiguration
title: HSM-Konfiguration
uuid: da4d7118-65a8-460d-a796-b7bf5c28b208
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# HSM-Konfiguration {#hsm-configuration}

Wenn Sie Ihre Serverberechtigungen mit einem HSM speichern möchten, müssen Sie die privaten Schlüssel und Zertifikate auf das HSM laden und eine [!DNL pkcs11.cfg] Konfigurationsdatei erstellen. Diese Datei muss sich im Ordner *LicenseServer.ConfigRoot* befinden. Eine Beispielkonfigurationsdatei für PKCS11 finden Sie im [!DNL Adobe Access Server for Protected Streaming/configs] Verzeichnis auf der Adobe Access DVD. Informationen zum Format [!DNL pkcs11.cfg]finden Sie in der Dokumentation zum Sun PKCS11-Anbieter.

Um sicherzustellen, dass die HSM- und Sun PKCS11-Konfigurationsdatei ordnungsgemäß konfiguriert sind, können Sie den folgenden Befehl aus dem Ordner verwenden, in dem sich die [!DNL pkcs11.cfg] Datei befindet ( [!DNL keytool] ist mit Java JRE und JDK installiert):

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldeinformationen in der Liste angezeigt werden, ist das HSM korrekt konfiguriert und der Lizenzserver kann auf die Anmeldeinformationen zugreifen.

> [!NOTE]
> Adobe Access Server für geschütztes Streaming unterstützt derzeit keine HSMs unter 64-Bit-Windows-Betriebssystemen.

