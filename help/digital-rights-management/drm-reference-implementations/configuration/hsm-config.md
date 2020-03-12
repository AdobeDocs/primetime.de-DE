---
description: Sie können die Referenz-Implementierung mit dem Sun PKCS#11-Anbieter konfigurieren, der HSM unterstützt. Die Verwendung eines HSM ist zwar nicht erforderlich, wird jedoch empfohlen.
seo-description: Sie können die Referenz-Implementierung mit dem Sun PKCS#11-Anbieter konfigurieren, der HSM unterstützt. Die Verwendung eines HSM ist zwar nicht erforderlich, wird jedoch empfohlen.
seo-title: HSM-Konfiguration
title: HSM-Konfiguration
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSM-Konfiguration{#hsm-configuration}

Sie können die Referenz-Implementierung mit dem Sun PKCS#11-Anbieter konfigurieren, der HSM unterstützt. Die Verwendung eines HSM ist zwar nicht erforderlich, wird jedoch empfohlen.

Um eine Berechtigung auf einem HSM zu verwenden, müssen Sie eine Konfigurationsdatei für den Sun PKCS#11-Anbieter erstellen. Weitere Informationen finden Sie im [Java PCKS#11 Referenzhandbuch](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

Um zu überprüfen, ob Ihre HSM- und Sun PKCS#11-Konfigurationsdatei konfiguriert sind, geben Sie den folgenden Befehl mit dem Keytool ein, das mit dem Java JDK installiert wurde:

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Sie haben das HSM korrekt konfiguriert, wenn Sie Ihre Anmeldeinformationen in der Liste Ansicht haben.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Ab Java 1.7 unterstützt Sun Java für Windows 64-Bit nicht mehr die PKCS#11-Schnittstellen, die Adobe Primetime DRM für die Kommunikation mit HSM-Geräten benötigt. Wenn Sie planen, ein HSM zu verwenden, stellen Sie sicher, dass Sie eine 32-Bit-Version von Java verwenden oder ein JDK verwenden, das die vollständigen PKCS#11-Schnittstellen unterstützt.

