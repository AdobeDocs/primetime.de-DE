---
description: CRS kann zeitgesteuerte ID3-Metadaten in das HLS-Format und kreative Elemente einfügen, um die clientseitige Anzeigenverfolgung zu erleichtern.
title: Verwenden von CRS zum Einfügen von ID3-Timed-Metadaten-Tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Verwenden von CRS zum Einfügen von ID3-Timed-Metadaten-Tags {#using-crs-to-inject-id-timed-metadata-tags}

CRS kann zeitgesteuerte ID3-Metadaten in das HLS-Format und kreative Elemente einfügen, um die clientseitige Anzeigenverfolgung zu erleichtern.

Der Client-Player liest die ID3-Metadaten, um eine Frame-genaue Anzeigenverfolgung zu ermöglichen.

>[!NOTE]
>
>Die zeitgesteuerte Metadaten-Injektion von ID3 funktioniert nur in Safari unter iOS.

## Workflow für CRS für ID3-Injektion {#workflow-for-crs-for-id3-injection}

Der Arbeitsablauf für die ID3-Injektion ist identisch mit dem in [Detaillierte Workflows für die JIT-Neuverpackung.](../~old-creative-repackaging-service/jit-repackage.md) Wenn der Manifestserver den  `ptplayer=ios-mobileweb` Parameter empfängt, weist er CRS an, ID3-Pakete in das transkodierte Werbemittel-Kreativelement zu injizieren, bevor dieser auf den CDN-Server hochgeladen wird.

>[!NOTE]
>
>Bei einem Multi-CDN-Setup verwendet der Manifestserver den Parameter `ptcdn` in der Bootstrap-URL, um den CDN-Server für das Hochladen des Werbekreativen zu identifizieren.