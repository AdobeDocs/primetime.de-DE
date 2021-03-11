---
description: Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie die Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.
title: Lokal generierte Zertifikatsperrlisten verwenden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Lokal generierte Zertifikatsperrlisten verwenden {#consuming-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie die Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.

Die folgenden APIs prüfen, ob die Listen nicht manipuliert wurden und ob die Listen vom richtigen Lizenzserver signiert wurden:

* Rufen Sie [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) für beliebige APIs bereitstellen.

   Weitere Informationen finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Rufen Sie [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie `PolicyUpdateList` für alle APIs bereitstellen.

   Weitere Informationen finden Sie unter [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

