---
title: Adobe Medien-Server verwenden
description: Adobe Medien-Server verwenden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 3%

---


# Adobe Mediums-Server {#use-adobe-media-server} verwenden

Einige Kunden verwenden möglicherweise bereits Adobe Mediums Server und möchten dieses Content Versand-Modell beibehalten. In diesem Fall können die erforderlichen DRM-spezifischen Primetime Cloud-Daten aus einer der Konfigurationsdateien, die in diesem Kit enthalten sind, abgerufen werden, um die JIT-XML-Konfiguration (Just-In-Time) für AMS zu füllen.

Beispiel:

```xml
<?xml version="1.0"?>
<Application>
  <HDS>
    <HLS>
      <Encryption enabled="true" protection-scheme="AdobeAccessV4">
        <AdobeAccessV4>
          <ContentID>SampleVideo</ContentID>
          <CommonKeyPath>common-key.bin</CommonKeyPath>
          <LicenseServerURL>
            https://access.adobeprimetime.com/flashaccessserver/axs_prod
          </LicenseServerURL>
          <KeyServerURL>
            https://access.adobeprimetime.com:443/faxsks/axs_prod/key
          </KeyServerURL>
          <TransportCertPath>cert/Cloud DRM-transport.cer</TransportCertPath>
          <LicenseServerCertPath>cert/Cloud DRM-license.cer</LicenseServerCertPath>
          <PackagerCredentialPath>cert-from-adobe.pfx</PackagerCredentialPath>
          <PackagerCredentialPwd>pass-for-cert-from-adobe</PackagerCredentialPwd>
          <PolicyPath>policy_ios_localkeyserver.pol</PolicyPath>
        </AdobeAccessV4>
      </Encryption>
    </HLS>
  </HDS>
</Application>
```

