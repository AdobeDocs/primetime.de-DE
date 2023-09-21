---
description: Sie können die Referenzimplementierung mit dem Sun PKCS#11-Provider konfigurieren, der HSM unterstützt. Obwohl die Verwendung eines HSM nicht erforderlich ist, wird empfohlen.
title: HSM-Konfiguration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# HSM-Konfiguration{#hsm-configuration}

Sie können die Referenzimplementierung mit dem Sun PKCS#11-Provider konfigurieren, der HSM unterstützt. Obwohl die Verwendung eines HSM nicht erforderlich ist, wird empfohlen.

Um eine Berechtigung auf einem HSM zu verwenden, müssen Sie eine Konfigurationsdatei für den Sun PKCS#11-Provider erstellen. Weitere Informationen finden Sie unter [Java PCKS#11 Referenzhandbuch](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

Um sicherzustellen, dass Ihre HSM- und Sun PKCS#11-Konfigurationsdatei konfiguriert sind, geben Sie den folgenden Befehl mithilfe des mit dem Java-JDK installierten Keytool ein:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Sie haben das HSM korrekt konfiguriert, wenn Sie Ihre Anmeldedaten in der Liste anzeigen können.

>[!NOTE]
>
>Ab Java 1.7 unterstützt Sun Java 64-Bit für Windows nicht mehr die PKCS#11-Schnittstellen, die Adobe Primetime DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie ein HSM verwenden möchten, stellen Sie sicher, dass Sie eine 32-Bit-Version von Java verwenden oder ein JDK verwenden, das die vollständigen PKCS#11-Schnittstellen unterstützt.
