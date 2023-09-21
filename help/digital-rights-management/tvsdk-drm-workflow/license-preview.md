---
title: Lizenzvorschau
description: Lizenzvorschau
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Lizenzvorschau {#license-preview}

Wenn es eine Frage gibt, ob ein Gerät eine Primetime DRM-Lizenz nutzen und vollständig durchsetzen kann, können Sie die Funktion &quot;Lizenzvorschau&quot;verwenden. Eine Vorschaulizenz entspricht vollständig allen in der endgültigen Lizenz definierten Einschränkungen und Einschränkungen, enthält jedoch nicht den Inhaltsverschlüsselungsschlüssel (Content Encryption Key, CEK), der zum Entschlüsseln des geschützten Inhalts erforderlich ist. Diese Funktion ist nützlich, um festzustellen, ob der Kunde die Lizenz tatsächlich nutzen kann, bevor der Inhaltsverteiler eine Entscheidung trifft, dem Kunden eine bestimmte Lizenz zu erteilen. Beispiel: Ein Kunde möchte HD-Inhalte sehen, aber der Content-Distributor möchte sicherstellen, dass das Gerät HDCP vollständig erkennen und ansprechen kann. In diesem Fall kann der Client `DRMManager.loadPreviewVoucher()`. Wenn eine `DRMStatusEvent` empfangen wird, anstatt `DRMErrorEvent`, dann wird bestätigt, dass der Kunde die Output Protection-Einschränkungen in der Lizenz vollständig durchsetzen kann und der Content Distributor diese Art von Lizenz dem Kunden kostenlos zur Verfügung stellen kann.

[iOS acquisitionPreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquisitionPreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
