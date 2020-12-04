---
seo-title: Vorschau der Lizenz
title: Vorschau der Lizenz
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Lizenz-Vorschau {#license-preview}

Wenn es eine Frage gibt, ob ein Gerät eine Primetime-DRM-Vorschau nutzen und vollständig durchsetzen kann, können Sie die Lizenzfunktion verwenden. Eine Vorschau-Lizenz entspricht voll und ganz allen Einschränkungen, die in der endgültigen Lizenz definiert sind, enthält jedoch nicht den Content Encryption Key (CEK), der zum Entschlüsseln des geschützten Inhalts benötigt wird. Diese Funktion ist nützlich, um festzustellen, ob der Kunde die Lizenz tatsächlich nutzen kann, bevor der Content-Distributor entscheidet, dem Kunden eine bestimmte Lizenz bereitzustellen. Zum Beispiel - ein Kunde möchte HD-Inhalte ansehen, aber der Content-Distributor möchte sicherstellen, dass das Gerät HDCP vollständig erkennen und einbinden kann. In diesem Fall kann der Client `DRMManager.loadPreviewVoucher()` aufrufen. Wenn anstelle von `DRMErrorEvent` ein `DRMStatusEvent` empfangen wird, wird bestätigt, dass der Client die Output Protection-Beschränkungen in der Lizenz vollständig durchsetzen kann und der Content-Distributor diese Art von Lizenz dem Client frei bereitstellen kann.

[iOS acquisitionPreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquisitionPreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
