---
title: Einrichten der Anzeigenverfolgung
description: Einrichten der Anzeigenverfolgung
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Einrichten der Anzeigenverfolgung {#ser-up-ad-tracking}

Die meisten Anzeigenkunden benötigen Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Primetime Ad Insertion unterstützt die clientseitige, serverseitige und hybride Anzeigenverfolgung, um diese Informationen flexibel zu erfassen.

## Clientseitige Anzeigenverfolgung mit VMAP/JSON {#client-side-ad-tracking-vmap-json}

Bei der clientseitigen Anzeigenverfolgung sendet der Server dem Client eine JSON-, VMAP- oder In-Manifest-Struktur, die Tracking-Ereignis und URLs zusammen mit der Anzeigenliste angibt.

Um die clientseitige Anzeigenverfolgung zu aktivieren, geben Sie die folgenden Parameter in der [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) an.

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>Wenn Sie `pttrackingmode=simple` festlegen, gibt die anfängliche Bootstrap-API-Anforderung eine JSON-Antwort zurück, nicht ein HLS- oder DASH-Dokument.

Weitere Informationen zu den Formaten `pttrackingmode`, `pttrackingversion` finden Sie in der [API-Referenz: Manifestserver-Abfragen-Parameter](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).

## Serverseitige Anzeigenverfolgung {#server-side-ad-tracking}

Mit dieser Methode werden Anzeigenverfolgungsdaten vollständig serverseitig berechnet. Dies ist nützlich, wenn eine Aktualisierung der Clientanwendung nicht möglich ist. Die serverseitige Anzeigenverfolgung stimmt jedoch möglicherweise nicht mit der clientseitigen Wiedergabe-Aktivität überein. So betrachtet der Server z. B. eine Anzeige als wiedergegeben, nachdem die Segmente bereitgestellt wurden, auch wenn der Endbenutzer die gesamte Anzeige nicht Ansicht.

Um die serverseitige Anzeigenverfolgung zu aktivieren, geben Sie den folgenden Parameter in der [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) an.

`pttrackingmode=sstm`

Siehe die Abschnitte `pttrackingmode` der [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).

Alle Anzeigenverfolgungsbeacons werden mit den folgenden HTTP-Anforderungsheader gesendet:

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Diese Werte enthalten den Client/Player-Benutzeragent und die Client-IP-Adresse.

## Hybride Anzeigenverfolgung {#hybrid-ad-tracking}

Dieser Ansatz ähnelt der serverseitigen Verfolgung, aber die Clientanwendung fordert auch Sidecars von Primetime Ad Insertion für detaillierte Verfolgungsinformationen an. Bei der Hybrid-Anzeigenverfolgung können nichtlineare Anzeigen wie Überlagerungen und Begleiter an die Client-Anwendung gesendet werden, wobei Primetime-Ad Insertion weiterhin darauf angewiesen ist, einzelne Anzeigen-Tracking-URLs zu senden.
Informationen zum Aktivieren der Hybrid-Anzeigenverfolgung finden Sie im Parameter `pttrackingmode` in der [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).
