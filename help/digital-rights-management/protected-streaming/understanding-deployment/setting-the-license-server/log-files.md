---
description: Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.
seo-description: Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.
seo-title: Protokolldateien
title: Protokolldateien
uuid: 4498fe60-65af-4f99-8f9b-e85013d0c9e9
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Protokolldateien{#log-files}

Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.

>[!NOTE]
>
>Wenn die aktuellen Protokolldateien während der Ausführung des Servers gelöscht oder verschoben werden, wird die Protokolldatei möglicherweise nicht erneut erstellt. Daher können einige Protokollinformationen gelöscht werden.

## Protokollordnerstruktur {#section_F490A483D60145ADBC21038914C39203}

Protokollordner sind für eine einfache Verwendung strukturiert. Der Protokollordner hat die folgende Struktur:

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

## Globale Protokolldatei {#section_1CFA90748142439C9F3BE380969539DA}

Die globale Protokolldatei `flashaccess-global.log` befindet sich unter *LicenseServer.LogRoot*. Das Protokoll kann Protokollmeldungen enthalten, die das Adobe Primetime DRM Java SDK oder Protokollmeldungen während der Zeit generiert haben, in der der Server initialisiert wurde.

## Partitionsprotokolldatei {#section_5660137CD6AA40519E72A4315534846B}

Die Partitionsprotokolldatei `flashaccess-partition.log` befindet sich im Ordner `<LicenseServer.LogRoot>/flashaccesserver`. Es enthält Protokollmeldungen, die während der Verarbeitung einer Lizenzanforderung generiert wurden.

## Mandanten-Protokolldatei {#section_F0257CC0831647F18A746B4F02E3E910}

Die Protokolldatei (`flashaccess-tenant.log`) jedes Mandanten befindet sich in `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Das Mandantenprotokoll enthält Informationen zum Audit, in denen jede für diesen Mandanten generierte Lizenz beschrieben wird.
