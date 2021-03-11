---
description: Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.
title: Protokolldateien
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
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
