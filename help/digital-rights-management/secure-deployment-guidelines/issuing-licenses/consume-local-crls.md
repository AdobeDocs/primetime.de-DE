---
description: Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.
seo-description: Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.
seo-title: Lokal generierte Zertifikatsperrlisten verwenden
title: Lokal generierte Zertifikatsperrlisten verwenden
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Lokal generierte Zertifikatsperrlisten verwenden {#consuming-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.

Die folgenden APIs prüfen, ob die Listen nicht manipuliert wurden und ob die Listen vom richtigen Lizenzserver signiert wurden:

* Rufen Sie [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie die [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) für alle APIs bereitstellen.

   Weitere Informationen finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Rufen Sie [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie sie für alle APIs bereitstellen `PolicyUpdateList` können.

   Weitere Informationen finden Sie unter [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

