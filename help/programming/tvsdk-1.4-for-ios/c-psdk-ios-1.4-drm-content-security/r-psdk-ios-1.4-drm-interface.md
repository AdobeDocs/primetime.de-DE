---
description: Das Client-seitige Schlüsselelement des Digital Rights Management (DRM)-Systems von Primetime ist der DRM Manager.
title: Übersicht über die Primetime-DRM-Oberfläche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Übersicht über die Primetime-DRM-Oberfläche {#primetime-drm-interface-overview}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime DRM-Lösung von Adobe verwenden.

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen über die Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

Das Client-seitige Schlüsselelement des Digital Rights Management (DRM)-Systems von Primetime ist der DRM Manager.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM bietet einen skalierbaren, effizienten Workflow zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie für jede digitale Mediendatei eine Lizenz erstellen.

TVSDK unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Authentifizierungs-Workflows implementieren muss, bevor der Stream mit dem Flash DRMManager wiedergegeben wird. Um dies zu aktivieren, stellt Ihnen der MediaPlayer den DRM-Manager zur Authentifizierung bereit.

Siehe DRM-Beispiel-Player-Code, der im TVSDK-Paket enthalten ist.

Dies sind die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

  ```
  @property (readonly, nonatomic) DRMManager *drmManager
  ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK-Probleme `PTMediaPlayerItemDRMMetadataChanged` Benachrichtigung bei Änderung der DRM-Metadaten. Diese Metadaten werden als Eingabe für fast alle Funktionen der `DRMManager` -Klasse.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Wenn der DRM-geschützte Stream mit mehreren Bit-Raten (MBR) kodiert ist, sollten die DRM-Metadaten, die für die Wiedergabeliste verwendet werden, mit den Metadaten übereinstimmen, die in allen Bitratenströmen verwendet werden.

>[!TIP]
>
>Beim Verweisen auf DRM-geschützte Asset-URLs in Ihrer iOS-App wird der Abfragezeichenfolgenparameter `?faxs=1` muss an die (MBR)-URL auf Setebene M3U8 angehängt werden. Beispiel:
>
>```
>https://your.domain.com/hls/[...]/index.m3u8?faxs=1
>```
>
>Die `faxs=1` Der Abfragezeichenfolgenparameter signalisiert, dass der Inhalt DRM-geschützt ist, und der DRM-Entschlüsselungs-Workflow wird entsprechend im iOS TVSDK Trigger. Sie können auch die `faxs=1` -Tag auf DRM-geschützten HLS-Asset-URLs platzieren, die für andere Plattformen bestimmt sind. Sie werden bei iOS als erforderlich beobachtet oder in Playern auf anderen Plattformen als Nicht-op behandelt.

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie im [Adobe Primetime DRM-Dokumentation](https://help.adobe.com/en_US/primetime/drm).

## Primetime DRM in eine TSVDK-Anwendung implementieren {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM ist in TVSDK integriert, was die Implementierung des Inhaltsschutzes in einer TVSDK-Anwendung vereinfacht.

Eine Übersicht und Details zur Verwendung von Primetime DRM zur Implementierung des Inhaltsschutzes in einer TVSDK-Anwendung finden Sie unter:

* [Adobe Primetime TVSDK-DRM-Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)
