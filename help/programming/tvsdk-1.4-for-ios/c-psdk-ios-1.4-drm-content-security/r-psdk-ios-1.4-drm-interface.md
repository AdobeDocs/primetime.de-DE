---
description: Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager.
seo-description: Das wichtigste clientseitige Element des DRM-Systems (Primetime Digital Rights Management) ist der DRM Manager.
seo-title: Übersicht über die Primetime-DRM-Oberfläche
title: Übersicht über die Primetime-DRM-Oberfläche
uuid: 3aae7c7a-fd0c-430e-9018-fd72801ab778
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Übersicht über die Primetime-DRM-Oberfläche {#primetime-drm-interface-overview}

Sie können die Funktionen des Primetime-Digital Rights Managements (DRM) verwenden, um einen sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ dazu können Sie auch DRM-Lösungen von Drittanbietern als Alternative zur integrierten Primetime-DRM-Lösung der Adobe verwenden.

Wenden Sie sich an Ihren Kundenbetreuer, um aktuelle Informationen zur Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

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

TVSDK gibt eine `PTMediaPlayerItemDRMMetadataChanged`-Benachrichtigung aus, wenn sich die DRM-Metadaten ändern. Diese Metadaten werden als Eingabe für fast alle Funktionen der `DRMManager`-Klasse verwendet.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Wenn der DRM-geschützte Stream mit mehreren Bitraten (MBR) kodiert ist, sollten die DRM-Metadaten, die für die Wiedergabeliste der Variante verwendet werden, mit den Metadaten übereinstimmen, die in allen Bitrate-Streams verwendet werden.

>[!TIP]
>
>Wenn Sie in Ihrer iOS-App auf DRM-geschützte Asset-URLs verweisen, muss der Abfrage-Zeichenfolgenparameter `?faxs=1` an die (MBR) URL auf Einstellungsebene M3U8 angehängt werden. Beispiel:
>
>
```
>https://your.domain.com/hls/[...]/index.m3u8?faxs=1
>```
>
>Der Zeichenfolgenparameter `faxs=1` gibt an, dass der Abfrage DRM-geschützt ist, und löst den DRM-Entschlüsselungs-Workflow im iOS TVSDK entsprechend aus. Sie können das `faxs=1`-Tag auch an DRM-geschützte HLS-Asset-URLs anhängen, die für andere Plattformen bestimmt sind. es wird unter iOS wie erforderlich beobachtet oder bei Playern auf anderen Plattformen als Nicht-Op behandelt.

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Weitere Informationen zu DRM finden Sie in der [Adobe Primetime DRM-Dokumentation](https://help.adobe.com/en_US/primetime/drm).

## Primetime-DRM in eine TSVDK-Anwendung {#implement-primetime-drm-in-a-tsvdk-application} implementieren

Primetime DRM ist in TVSDK integriert, was die Implementierung des Inhaltsschutzes in einer TVSDK Anwendung vereinfacht.

Eine Übersicht und Einzelheiten zur Verwendung von Primetime DRM zur Implementierung des Inhaltsschutzes in einer TVSDK-Anwendung finden Sie unter:

* [Adobe Primetime TVSDK-DRM Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)