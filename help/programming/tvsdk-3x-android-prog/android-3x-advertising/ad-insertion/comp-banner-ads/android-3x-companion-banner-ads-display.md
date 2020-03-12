---
description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und TVSDK erlauben, auf anzeigenbezogene Ereignis zu hören.
seo-description: Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und TVSDK erlauben, auf anzeigenbezogene Ereignis zu hören.
seo-title: Anzeigen von Bannerwerbung
title: Anzeigen von Bannerwerbung
uuid: cfd4b26c-9643-4b60-9aff-bc27dec289f1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Anzeigen von Bannerwerbung {#display-banner-ads}

Um Banneranzeigen anzuzeigen, müssen Sie Bannerinstanzen erstellen und TVSDK erlauben, auf anzeigenbezogene Ereignis zu hören.

TVSDK bietet eine Liste von begleitenden Banneranzeigen, die über das `AdPlaybackEventListener.onAdBreakStart` Ereignis mit einer linearen Anzeige verbunden sind.

Manifeste können begleitende Banneranzeigen wie folgt angeben:

* Ein HTML-Snippet
* Die URL einer iFrame-Seite
* Die URL eines statischen Bildes oder einer Adobe Flash SWF-Datei

Für jede Begleitanzeige gibt TVSDK an, welche Typen für Ihre Anwendung verfügbar sind.

1. Hinzufügen Sie einen Listener für das `AdPlaybackEventListener.onAdBreakStart` Ereignis, das Folgendes ausführt:

   * Löscht vorhandene Anzeigen in der Bannerinstanz.
   * Ruft die Liste der begleitenden Anzeigen ab `Ad.getCompanionAssets`.
   * Wenn die Liste der begleitenden Anzeigen nicht leer ist, müssen Sie die Liste für Bannerinstanzen durchlaufen.

      Jede Bannerinstanz (ein `AdAsset`) enthält Informationen wie Breite, Höhe, Ressourcentyp (html, iframe oder statisch) und Daten, die zum Anzeigen des begleitenden Banners erforderlich sind.
   * Wenn bei einer Videoanzeige keine begleitenden Anzeigen gebucht wurden, enthält die Liste der begleitenden Assets keine Daten für diese Videoanzeige.
   * Um eine eigenständige Anzeige anzuzeigen, fügen Sie die Logik zu Ihrem Skript hinzu, um ein normales DFP (DoubleClick for Publishers)-Display-Tag in der entsprechenden Bannerinstanz auszuführen.
   * Sendet die Bannerinformationen an eine Funktion auf Ihrer Seite, die die Banner an einer geeigneten Position anzeigt.

      Dies ist in der Regel ein `div`und Ihre Funktion verwendet das `div ID` , um das Banner anzuzeigen.