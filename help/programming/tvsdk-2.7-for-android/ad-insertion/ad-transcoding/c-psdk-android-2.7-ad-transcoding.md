---
description: Einige Drittanbieter-Anzeigen (oder Kreative) können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingebunden werden, da ihr Videoformat mit HLS inkompatibel ist. Primetime-Anzeigeneinfügung und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
title: Komprimieren Sie inkompatible Anzeigen mit dem Adobe Creative Repackaging Service (CRS) neu.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Komprimieren Sie inkompatible Anzeigen mit dem Adobe Creative Repackaging Service (CRS) neu. {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Einige Drittanbieter-Anzeigen (oder Kreative) können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingebunden werden, da ihr Videoformat mit HLS inkompatibel ist. Primetime-Anzeigeneinfügung und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Inventarpartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie dem progressiven Download-MP4-Format bereitgestellt.

Wenn TVSDK erstmals auf eine inkompatible Anzeige trifft, ignoriert der Player die Anzeige und sendet eine Anfrage an den CRS (Creative Repackaging Service), der Teil des Primetime-Anzeigeneinfüge-Backend ist, um die Anzeige in ein kompatibles Format zu verpacken. CRS versucht, M3U8-Ausgabeformate der Anzeige mit mehreren Bitraten zu generieren und speichert diese Ausgabeformate im Primetime Content Delivery Network (CDN). Wenn TVSDK das nächste Mal eine Anzeigenantwort erhält, die auf diese Anzeige verweist, verwendet der Player die HLS-kompatible M3U8-Version aus dem CDN.

Wenden Sie sich zur Aktivierung dieser optionalen CRS-Funktion an Ihren Adobe-Support-Mitarbeiter.

>[!NOTE]
>
>Kunden von CRS Version 3.0 (und früher), beginnend mit CRS Version 3.1, haben die folgenden Änderungen sowohl die Sicherheit als auch die Leistung verbessert:
>
>* CRS 3.1 wird mit `https:` wenn der neu verpackte Inhalt verwendet `https:`. Dadurch wird das Potenzial einiger Player verringert, unsichere Inhalte zu präsentieren.
>
>* CRS 3.1 minimiert Netzwerkaufrufe erheblich und verbessert so die Startzeit des Videos.
>

Weitere Informationen zu CRS finden Sie unter [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_certificate_enrollment.pdf).

## Aktivieren von CRS in TVSDK-Anwendungen{#enable-crs-in-tvsdk-applications}

Um CRS in Ihren TVSDK-Anwendungen zu aktivieren, müssen Sie die folgenden Informationen in Ihren Auditude-Einstellungen festlegen:

1. Aktivieren Sie CRS in `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
