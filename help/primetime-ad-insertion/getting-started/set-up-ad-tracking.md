---
title: Einrichten des Anzeigen-Trackings
description: Einrichten der Anzeigenverfolgung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Einrichten des Anzeigen-Trackings {#ser-up-ad-tracking}

Die meisten Advertiser benötigen Informationen darüber, wann, wie lange und wie erfolgreich ihre Anzeigen angesehen wurden. Primetime Ad Insertion unterstützt clientseitiges, serverseitiges und hybrides Anzeigen-Tracking, um Flexibilität bei der Erfassung dieser Informationen zu bieten.

## Clientseitige Anzeigenverfolgung mit VMAP/JSON {#client-side-ad-tracking-vmap-json}

Beim clientseitigen Anzeigen-Tracking sendet der Server dem Client eine JSON-, VMAP- oder In-Manifest-Struktur, die Tracking-Ereignisse und URLs zusammen mit der Anzeigenzuordnungsliste angibt.

Um das clientseitige Anzeigen-Tracking zu aktivieren, geben Sie die folgenden Parameter in der [Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>Festlegen der `pttrackingmode=simple` führt dazu, dass die anfängliche Bootstrap-API-Anfrage eine JSON-Antwort zurückgibt und nicht ein HLS- oder DASH-Dokument.

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## Serverseitige Anzeigenverfolgung {#server-side-ad-tracking}

Bei Verwendung dieser Methode werden die Anzeigen-Tracking-Daten vollständig serverseitig berechnet. Dies ist nützlich, wenn eine Aktualisierung der Clientanwendung nicht möglich ist. Das serverseitige Anzeigen-Tracking stimmt jedoch möglicherweise nicht mit der clientseitigen Wiedergabe-Aktivität überein. Beispielsweise betrachtet der Server eine Anzeige als wiedergegeben, nachdem die Segmente bereitgestellt wurden, selbst wenn der Endbenutzer die gesamte Anzeige nicht anzeigt.

Um die serverseitige Anzeigenverfolgung zu aktivieren, geben Sie den folgenden Parameter in der [Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

Siehe `pttrackingmode` Abschnitte von [Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

Alle Anzeigen-Tracking-Beacons werden mit den folgenden HTTP-Anforderungsheadern gesendet:

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Diese Werte enthalten die Client/Player-Benutzer-Agent- und Client-IP-Adresse.

## Hybrides Anzeigen-Tracking {#hybrid-ad-tracking}

Dieser Ansatz ähnelt dem serverseitigen Tracking, aber die Client-Anwendung fordert von Primetime Ad Insertion auch Seitenautos für detaillierte Tracking-Informationen an. Beim Hybrid-Anzeigen-Tracking können nichtlineare Anzeigen wie Überlagerungen und Begleiter an die Client-Anwendung gesendet werden, wobei für das Senden einzelner Anzeigen-Tracking-URLs an Primetime Ad Insertion erforderlich ist.
Informationen zum Aktivieren des Hybrid-Anzeigen-Trackings finden Sie im Abschnitt `pttrackingmode` -Parameter in der [Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).
