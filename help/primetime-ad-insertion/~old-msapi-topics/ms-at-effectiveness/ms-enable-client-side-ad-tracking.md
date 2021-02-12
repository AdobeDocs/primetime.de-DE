---
description: Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie die Parameter pttrackingmode und pttrackingversion zu Ihrer Bootstrap-URL-Anforderung hinzufügen.
seo-description: Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie die Parameter pttrackingmode und pttrackingversion zu Ihrer Bootstrap-URL-Anforderung hinzufügen.
seo-title: Aktivieren der clientseitigen Anzeigenverfolgung
title: Aktivieren der clientseitigen Anzeigenverfolgung
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 1%

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
