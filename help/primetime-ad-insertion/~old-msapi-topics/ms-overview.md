---
description: Der Manifestserver koordiniert die Systeme, die Inhalte bereitstellen, Anzeigen bereitstellen, Videos abspielen und Anzeigen verfolgen. Es empfängt M3U8-kodierte Playlisten (Manifeste), die Client-Videoplayer von Inhaltsanbietern erhalten, fügt Anzeigen von Anzeigenanbietern in die Manifeste ein und gibt die zugewiesenen Manifeste an Videoplayer weiter. Es unterstützt sowohl clientseitige als auch serverseitige Anzeigenverfolgung. Es führt seine Interaktionen über eine HTTP-basierte Webdienst-Schnittstelle durch.
title: Übersicht über Manifest Server-Interaktionen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Übersicht über Manifest-Server-Interaktionen {#overview-of-manifest-server-interactions}

Der Manifestserver koordiniert die Systeme, die Inhalte bereitstellen, Anzeigen bereitstellen, Videos abspielen und Anzeigen verfolgen. Es empfängt M3U8-kodierte Playlisten (Manifeste), die Client-Videoplayer von Inhaltsanbietern erhalten, fügt Anzeigen von Anzeigenanbietern in die Manifeste ein und gibt die zugewiesenen Manifeste an Videoplayer weiter. Es unterstützt sowohl clientseitige als auch serverseitige Anzeigenverfolgung. Es führt seine Interaktionen über eine HTTP-basierte Webdienst-Schnittstelle durch.

Eine typische Konfiguration enthält:

* Primetime-Manifestserver
* Der Primetime Creative Repackage Service (CRS)
* Ein Client, der einen Videoplayer steuert
* Ein Herausgeber, in der Regel mit einem Content-Management-System (CMS)
* Ein Content Versand Network (CDN)
* Ein Anzeigenserver
* Empfänger für Anzeigenverfolgungsberichte

Der Arbeitsablauf variiert je nach Anzahl der Faktoren, z. B. wenn das CDN Akamai ist oder der Client eine Anzeigenverfolgung durchführt. Eine Darstellung des Workflows zur clientseitigen Anzeigenverfolgung finden Sie unter [Client-seitigen Verfolgungsarbeitsablauf](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md#section_cst_flow).

Der Manifestserver interagiert mit Video-Versand-Clients, indem er HTTP-GET empfängt und darauf reagiert. Die Antworten sind M3U8-kodierte Manifeste, die anzeigeingenähten Inhalt beschreiben, optional einschließlich einer JSON- oder VMAP-Struktur (Sidecar) mit detaillierten Anweisungen zur Anzeigenverfolgung (siehe [Dateiformate](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).

Ein typischer Workflow sieht wie folgt aus:

1. Der Herausgeber sendet die Inhalts-URL und die Informationen für den Anzeigen-Server an den Client.
1. Der Client verwendet die Informationen des Herausgebers, um eine Manifestserver-URL zu generieren, und sendet eine GET an diese URL. Dies wird als Bootstrap-URL bezeichnet.
1. Der Manifestserver richtet eine Sitzung mit dem Client ein.
1. Der Manifestserver ruft Inhaltsmanifeste vom CDN ab, die Informationen zu Werbeunterbrechungen enthalten können.
1. Der Manifestserver leitet den Client an das Übergeordnet-/Variantenmanifest weiter, das er für den Client generiert hat.

   >[!NOTE]
   >
   >Wenn die Parameter für die Bootstrap-URL-Abfrage die Einstellung `pttrackingmode=simple` oder `ptplayer=ios-mobileweb` enthalten, gibt der Manifestserver die Übergeordnet/Variante-Manifest-URL in einem JSON-Objekt zurück und der Client sendet eine GET an diese Manifest-URL der Variante.

1. Der Client wählt einen Stream im generierten Variantenmanifest zur Wiedergabe aus und sendet Anzeigeninformationen an den Manifestserver.
1. Der Manifestserver leitet die vom Client bereitgestellten Informationen an den Anzeigen-Server weiter und empfängt Anzeigen und Anzeigen-Tracking-URLs vom Anzeigen-Server. Wenn eine bereitgestellte Anzeige nicht im HLS-Format vorliegt, sendet der Manifestserver sie zur Konvertierung in HLS an CRS.
1. Der Manifestserver ordnet Anzeigen in das Inhaltsmanifest ein und sendet das neue zugewiesene Manifest an den Client.
1. Der Client gibt den Inhalt mit den eingefügten Anzeigen wieder und sendet zu den angegebenen Zeitpunkten Anforderungen an die angegebenen Tracking-URLs.

Primetime-Anzeigen unterstützen Clients auf vielen Video-Versand-Plattformen. Nicht alle Clients basieren auf dem Primetime TVSDK-Paket, sondern alle Clients senden GET an die gleiche URL. Abfrage-Parameter unterscheiden eine Client-Anforderung von einer anderen, indem sie dem Manifestserver Folgendes mitteilen:

* welcher Kunde die Anforderung stellt,
* was der Kunde will,
* und welche Anzeigenverfolgungsinformationen bereitgestellt werden.

## CORS {#section_BEA7F298660944BE92801E4C82FCD038}

Der Manifestserver verwendet den Cross-Herkunft Resource Sharing Standard (CORS). Es wird nach einem `Origin`-Header in den Anforderungen gesucht, die es erhält. Wenn die Kopfzeile vorhanden ist, wird sie mit

* `Access-Control-Allow-Origin: *`Zeichenfolge aus der Kopfzeile der Herkunft`*`
* `Access-Control-Allow-Credentials: true`
* `Access-Control-Allow-Methods: GET`

Falls nicht, antwortet sie mit:

* `Access-Control-Allow-Origin: *`
* `Access-Control-Allow-Methods: GET`