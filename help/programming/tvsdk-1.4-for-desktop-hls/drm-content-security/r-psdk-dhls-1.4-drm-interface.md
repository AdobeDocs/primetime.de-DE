---
description: Das Client-seitige Schlüsselelement des Digital Rights Management (DRM)-Systems von Primetime ist der DRM Manager.
title: Übersicht über die Primetime-DRM-Oberfläche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Übersicht über die Primetime-DRM-Oberfläche{#primetime-drm-interface-overview}

Das Client-seitige Schlüsselelement des Digital Rights Management (DRM)-Systems von Primetime ist der DRM Manager.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM bietet einen skalierbaren, effizienten Workflow zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie für jede digitale Mediendatei eine Lizenz erstellen.

TVSDK unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Authentifizierungs-Workflows implementieren muss, bevor der Stream mithilfe der Flash wiedergegeben wird `DRMManager`. Um dies zu aktivieren, muss die Variable `MediaPlayer` stellt Ihnen den DRM-Manager zur Authentifizierung zur Verfügung.

Dies sind die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

  ```
  public function get drmManager():DRMManager 
  ```

<!--<a id="section_4204CE2731A44F67A3664AEDE8CCCA47"></a>-->

Zusätzliche relevante API-Elemente:

* [flash.net.drm.DRMManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html)
* [flash.net.drm.DRMContentData](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMContentData.html)
* [flash.net.drm.DRMVoucher](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMVoucher.html)
* [flash.net.drm.AuthenticationMethod](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/AuthenticationMethod.html)
* [flash.events.DRMStatusEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMStatusEvent.html)
* [flash.events.DRMErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMErrorEvent.html)

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie in der Adobe Primetime DRM-Dokumentation.
