---
description: Just-in-time-Transkodierung kann zeitgesteuerte ID3-Metadaten in Werbeinhalte injizieren, um die clientseitige Anzeigenverfolgung zu erleichtern.
title: Verwenden der Just-in-time-Transkodierung zum Einfügen von ID3-Timed-Metadaten-Tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Verwenden der Just-in-time-Transkodierung zum Einfügen von ID3-Timed-Metadaten-Tags {#using-crs-to-inject-id-timed-metadata-tags}

Mit CRS können zeitgesteuerte ID3-Metadaten in Werbekreative eingefügt werden, um die clientseitige Anzeigenverfolgung zu erleichtern.

Der Client-Player liest die ID3-Metadaten, um eine Frame-genaue Anzeigenverfolgung zu ermöglichen.

>[!NOTE]
>
>ID3-Funktionen zum Einschleusen von Metadaten nur für Safari/iOS.

## Workflow für CRS für ID3-Injektion {#workflow-for-crs-for-id3-injection}

Wenn Primetime Ad Insertion den Parameter `ptplayer=ios-mobileweb` erhält, injiziert es ID3-Pakete in das transkodierte Werbekreativ, bevor es in das entsprechende Ad-Datenspeicherung-CDN hochgeladen wird.
