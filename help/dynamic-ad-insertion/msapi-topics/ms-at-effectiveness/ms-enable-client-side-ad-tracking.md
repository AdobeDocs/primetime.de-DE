---
description: Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie der Bootstrap-URL-Anforderung die Parameter pttrackingmode und pttrackingversion hinzufügen.
seo-description: Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie der Bootstrap-URL-Anforderung die Parameter pttrackingmode und pttrackingversion hinzufügen.
seo-title: Aktivieren der clientseitigen Anzeigenverfolgung
title: Aktivieren der clientseitigen Anzeigenverfolgung
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Aktivieren der clientseitigen Anzeigenverfolgung {#enable-client-side-ad-tracking}

Sie können die clientseitige Anzeigenverfolgung aktivieren, indem Sie der Bootstrap-URL-Anforderung die Parameter `pttrackingmode` und `pttrackingversion` hinzufügen.

Wenn die clientseitige Anzeigenverfolgung aktiviert ist, können Sie auch Anzeigenverfolgungsmetadaten mithilfe der Tracking-API-URL abrufen. Weitere Informationen finden Sie unter [Abfrage-Parameter](../../msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md).

Verwenden Sie zur clientseitigen Anzeigenverfolgung die Tracking-API-URL.

1. Hinzufügen Sie die folgenden Abfragen an die URL der Manifestserveranforderung an:

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Beispiel:

```
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
