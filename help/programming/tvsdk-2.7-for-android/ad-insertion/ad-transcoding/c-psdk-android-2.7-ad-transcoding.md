---
description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-description: Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.
seo-title: Komprimieren Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service (CRS).
title: Komprimieren Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service (CRS).
uuid: c3961628-39aa-444c-9c93-9f1e267d9cd4
translation-type: tm+mt
source-git-commit: 1859eb201a41797544fee1ad97d5cb21c7a0a7c1

---


# Komprimieren Sie inkompatible Anzeigen mit dem Adobe Creative Repackage Service (CRS). {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Einige Anzeigen (oder kreative Elemente) von Drittanbietern können nicht in den HTTP Live Streaming (HLS)-Inhaltsstream eingefügt werden, da ihr Videoformat mit HLS nicht kompatibel ist. Primetime-Anzeigen und TVSDK können optional versuchen, inkompatible Anzeigen in kompatible M3U8-Videos zu verpacken.

Anzeigen, die von verschiedenen Drittanbietern bereitgestellt werden, z. B. von einer Agentur und einem Server, Ihrem Bestandspartner oder einem Werbenetzwerk, werden häufig in inkompatiblen Formaten wie dem progressiven Download im MP4-Format bereitgestellt.

Wenn TVSDK zum ersten Mal auf eine inkompatible Anzeige stößt, ignoriert der Player die Anzeige und sendet eine Anforderung an den Kreativ-Umverpackungsdienst (CRS), der Teil des Primetime-Anzeigenende ist, um die Anzeige in ein kompatibles Format zu verpacken. CRS versucht, M3U8-Darstellungen der Anzeige mit mehreren Bitraten zu generieren, und speichert diese Darstellungen im Primetime Content Versand Network (CDN). Wenn TVSDK das nächste Mal eine Anzeigenantwort erhält, die auf diese Anzeige verweist, verwendet der Player die HLS-kompatible M3U8-Version vom CDN.

Wenden Sie sich zur Aktivierung dieser optionalen CRS-Funktion an Ihren Adobe-Kundenbetreuer.

>[!NOTE]
>
>Für Kunden mit CRS Version 3.0 (und früher) haben die folgenden Änderungen ab CRS Version 3.1 sowohl die Sicherheit als auch die Leistung verbessert: >
>* CRS 3.1 wird weiterhin verwendet, `https:` wenn der neu verpackte Inhalt verwendet `https:`. Dadurch wird das Potenzial einiger Player verringert, unsichere Inhalte zu präsentieren.
   >
   >
* Mit CRS 3.1 werden Netzwerkaufrufe erheblich minimiert, wodurch die Zeit des Videostarts erheblich verkürzt wird.
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
