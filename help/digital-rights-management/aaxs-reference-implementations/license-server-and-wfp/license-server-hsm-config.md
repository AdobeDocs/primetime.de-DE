---
seo-title: HSM-Konfiguration
title: HSM-Konfiguration
uuid: 1cc5be99-c24c-4c1e-9348-fb69f96d8ca5
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# HSM-Konfiguration {#hsm-configuration}

Die Verwendung eines HSM ist nicht erforderlich, wird jedoch empfohlen. Die Referenzimplementierung kann so konfiguriert werden, dass der Sun PKCS11-Anbieter für HSM-Unterstützung verwendet wird. Um eine Berechtigung für ein HSM zu verwenden, müssen Sie eine Konfigurationsdatei für den Sun PKCS11-Anbieter erstellen. Weitere Informationen finden Sie in der Sun-Dokumentation. Um sicherzustellen, dass die HSM- und Sun PKCS11-Konfigurationsdatei ordnungsgemäß konfiguriert sind, können Sie den folgenden Befehl verwenden (das Keytool wird mit dem Java JDK installiert):

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Wenn Ihre Anmeldedaten in der Liste angezeigt werden, ist das HSM korrekt konfiguriert.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64-Bit nicht die PKCS11-Schnittstellen, die Adobe Access DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, verwenden Sie bitte eine 32-Bit-Version von Java oder ein JDK, das die vollständige PKCS11-Schnittstelle unterstützt.

