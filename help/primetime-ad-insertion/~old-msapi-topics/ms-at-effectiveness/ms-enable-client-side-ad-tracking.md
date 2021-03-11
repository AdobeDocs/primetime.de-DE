---
description: Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie die Parameter pttrackingmode und pttrackingversion zu Ihrer Bootstrap-URL-Anforderung hinzufügen.
title: Aktivieren der clientseitigen Anzeigenverfolgung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 2%

---


# Aktivieren der clientseitigen Anzeigenverfolgung {#enable-client-side-ad-tracking}

Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie die Parameter `pttrackingmode` und `pttrackingversion` zu Ihrer Bootstrap-URL-Anforderung hinzufügen.

Wenn die clientseitige Anzeigenverfolgung aktiviert ist, können Sie auch Anzeigenverfolgungsmetadaten mithilfe der Tracking-API-URL abrufen. Weitere Informationen finden Sie unter [Abfragen-Parameter](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md).

Verwenden Sie zur clientseitigen Anzeigenverfolgung die Tracking-API-URL.

1. hinzufügen Sie die folgenden Abfragen an die URL der Manifestserveranforderung an:

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Beispiel:

```URL
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
