---
description: Just-in-time-Transkodierung kann zeitgesteuerte ID3-Metadaten in Werbeinhalte injizieren, um die clientseitige Anzeigenverfolgung zu erleichtern.
seo-description: Just-in-time-Transkodierung kann ID3-zeitgesteuerte Metadaten in das HLS-Format und kreative Elemente injizieren, um die clientseitige Anzeigenverfolgung zu erleichtern.
seo-title: Verwenden der Just-in-time-Transkodierung zum Einfügen von ID3-Timed-Metadaten-Tags
title: Verwenden der Just-in-time-Transkodierung zum Einfügen von ID3-Timed-Metadaten-Tags
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '121'
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
