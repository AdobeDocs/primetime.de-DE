---
description: Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager.
seo-description: Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager.
seo-title: Übersicht über die Primetime-DRM-Oberfläche
title: Übersicht über die Primetime-DRM-Oberfläche
uuid: 3aae7c7a-fd0c-430e-9018-fd72801ab778
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# Übersicht über die Primetime-DRM-Oberfläche {#primetime-drm-interface-overview}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime-DRM-Lösung von Adobe verwenden.

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen zur Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM bietet einen skalierbaren, effizienten Arbeitsablauf zur Implementierung des Inhaltsschutzes in TVSDK-Anwendungen. Sie schützen und verwalten die Rechte an Ihren Videoinhalten, indem Sie eine Lizenz für jede digitale Mediendatei erstellen.

TVSDK unterstützt die Primetime DRM-Integration als benutzerdefinierte DRM-Workflows. Das bedeutet, dass Ihre Anwendung die DRM-Workflows implementieren muss, bevor der Stream mit dem Flash DRMManager wiedergegeben wird. Um dies zu aktivieren, stellt der MediaPlayer Ihnen den DRM-Manager zur Authentifizierung zur Verfügung.

Siehe DRM-Beispielplayer-Code im TVSDK-Paket.

Dies sind die wichtigsten API-Elemente für die Arbeit mit DRM:

* Ein Verweis im Medienplayer auf das DRM-Manager-Objekt, das das DRM-Subsystem implementiert:

   ```
   @property (readonly, nonatomic) DRMManager *drmManager
   ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK gibt eine `PTMediaPlayerItemDRMMetadataChanged` Benachrichtigung aus, wenn sich die DRM-Metadaten ändern. Diese Metadaten werden als Eingabe für fast alle Funktionen der `DRMManager` Klasse verwendet.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Wenn der DRM-geschützte Stream mit mehreren Bitraten (MBR) kodiert ist, sollten die DRM-Metadaten, die für die Wiedergabeliste der Variante verwendet werden, mit den Metadaten übereinstimmen, die in allen Bitrate-Streams verwendet werden.

>[!TIP] {important=&quot;high&quot;}
>
>Wenn Sie in Ihrer iOS-App auf DRM-geschützte Asset-URLs verweisen, `?faxs=1` muss der Parameter für die Zeichenfolge der Abfrage an die (MBR) URL auf Einstellungsebene M3U8 angehängt werden. Beispiel: >
>
```>
>https://your.domain.com/hls/[...]/index.m3u8?faxs=1
>```>
>The `faxs=1` query string parameter signals that the content is DRM protected, and triggers the DRM decryption workflow accordingly in the iOS TVSDK. You can also append the `faxs=1` tag on DRM-protected HLS asset URLs that are destined for other platforms; it is observed as required on iOS or treated as a non-op in players on other platforms.



<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie in der [Adobe Primetime DRM-Dokumentation](https://help.adobe.com/en_US/primetime/drm).

## Primetime DRM in eine TSVDK-Anwendung implementieren {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM ist in TVSDK integriert, was die Implementierung des Inhaltsschutzes in einer TVSDK Anwendung vereinfacht.

Eine Übersicht und Einzelheiten zur Verwendung von Primetime DRM zur Implementierung des Inhaltsschutzes in einer TVSDK-Anwendung finden Sie unter:

* [Adobe Primetime TVSDK-DRM Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)