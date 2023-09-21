---
description: Die Just-in-time-Transkodierung kann zeitgesteuerte ID3-Metadaten in Anzeigenkreativen einfügen, um das Tracking clientseitiger Anzeigen zu erleichtern.
title: Verwenden der Just-in-time-Transkodierung zum Einfügen von ID3-Tags mit zeitgesteuerten Metadaten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Verwenden der Just-in-time-Transcodierung zum Einfügen von ID3-Tags mit zeitgesteuerten Metadaten {#using-crs-to-inject-id-timed-metadata-tags}

CRS kann zeitgesteuerte ID3-Metadaten in Anzeigenkreativen einfügen, um das Tracking clientseitiger Anzeigen zu erleichtern.

Der Client-Player liest die ID3-Metadaten, um das frame-genaue Anzeigen-Tracking zu ermöglichen.

>[!NOTE]
>
>Die zeitgesteuerte Injektion von ID3-Metadaten funktioniert nur für Safari/iOS.

## Workflow für CRS für die ID3-Injektion {#workflow-for-crs-for-id3-injection}

Wenn Primetime Ad Insertion erhält `ptplayer=ios-mobileweb` -Parameter wird ID3-Pakete in das transkodierte Anzeigenmotiv injiziert, bevor sie auf das entsprechende Anzeigen-Speicher-CDN hochgeladen werden.
