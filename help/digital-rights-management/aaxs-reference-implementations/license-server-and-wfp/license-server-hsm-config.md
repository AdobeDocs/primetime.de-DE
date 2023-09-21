---
title: HSM-Konfiguration
description: HSM-Konfiguration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# HSM-Konfiguration {#hsm-configuration}

Die Verwendung eines HSM ist nicht erforderlich, wird jedoch empfohlen. Die Referenzimplementierung kann so konfiguriert werden, dass der Sun PKCS11-Provider für HSM-Unterstützung verwendet wird. Um eine Berechtigung auf einem HSM zu verwenden, müssen Sie eine Konfigurationsdatei für den Sun PKCS11-Provider erstellen. Weitere Informationen finden Sie in der Sun-Dokumentation . Um sicherzustellen, dass die Konfigurationsdatei für HSM und Sun PKCS11 ordnungsgemäß konfiguriert ist, können Sie den folgenden Befehl verwenden (das Keytool wird mit dem Java-JDK installiert):

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldedaten in der Liste angezeigt werden, ist das HSM ordnungsgemäß konfiguriert.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java 64-Bit für Windows nicht die PKCS11-Schnittstellen, die Adobe Access DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, verwenden Sie bitte eine 32-Bit-Version von Java oder ein JDK, das die vollständigen PKCS11-Schnittstellen unterstützt.
