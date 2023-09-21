---
description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass TVSDK auf anzeigenbezogene Ereignisse überwacht.
title: Anzeigen von Banneranzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Anzeigen von Banneranzeigen {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und zulassen, dass TVSDK auf anzeigenbezogene Ereignisse überwacht.

TVSDK bietet eine Liste mit begleitenden Banneranzeigen, die über die `AdPlaybackEventListener.onAdBreakStart` -Ereignis.

Manifeste können begleitende Banneranzeigen wie folgt spezifizieren:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL eines statischen Bildes oder einer Adobe-Flash-SWF-Datei

TVSDK gibt für jede begleitende Anzeige an, welche Typen für Ihre Anwendung verfügbar sind.

1. Fügen Sie einen Listener für die `AdPlaybackEventListener.onAdBreakStart` -Ereignis, das Folgendes ausführt:

   * Löscht vorhandene Anzeigen in der Bannerinstanz.
   * Ruft die Liste der begleitenden Anzeigen von ab `Ad.getCompanionAssets`.
   * Wenn die Liste der begleitenden Anzeigen nicht leer ist, navigieren Sie für Bannerinstanzen über die Liste.

     Jede Bannerinstanz (eine `AdAsset`) Informationen wie Breite, Höhe, Ressourcentyp (HTML, iframe oder statisch) sowie Daten enthält, die zum Anzeigen des begleitenden Banners erforderlich sind.
   * Wenn für eine Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.
   * Um eine eigenständige Display-Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP-Display-Anzeigen-Tag (DoubleClick for Publishers) in der entsprechenden Bannerinstanz auszuführen.
   * Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Stelle anzeigt.

     Dies ist normalerweise ein `div`und Ihre -Funktion verwendet die `div ID` , um das Banner anzuzeigen.
