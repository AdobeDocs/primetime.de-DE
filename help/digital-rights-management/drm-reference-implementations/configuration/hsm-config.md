---
description: Sie können die Referenz-Implementierung mit dem Sun PKCS#11-Anbieter konfigurieren, der HSM unterstützt. Die Verwendung eines HSM ist zwar nicht erforderlich, wird jedoch empfohlen.
seo-description: Sie können die Referenz-Implementierung mit dem Sun PKCS#11-Anbieter konfigurieren, der HSM unterstützt. Die Verwendung eines HSM ist zwar nicht erforderlich, wird jedoch empfohlen.
seo-title: HSM-Konfiguration
title: HSM configuration
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# HSM-Konfiguration{#hsm-configuration}

You can configure the reference implementation with the Sun PKCS#11 provider that supports HSM. Although the use of an HSM is not required, it is recommended.

To use a credential on an HSM, you must create a configuration file for the Sun PKCS#11 provider. For more information, see the [Java PCKS#11 Reference Guide](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

To verify that your HSM and Sun PKCS#11 configuration file are configured, type the following command by using the keytool that was installed with the Java JDK:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

You have configured the HSM correctly if you can view your credentials in the list.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64-Bit nicht mehr die PKCS#11-Schnittstellen, die Adobe Primetime DRM für die Kommunikation mit HSM-Geräten benötigt. If you plan to use an HSM, ensure that you use a 32-bit version of Java or use a JDK that supports the full PKCS#11 interfaces.

