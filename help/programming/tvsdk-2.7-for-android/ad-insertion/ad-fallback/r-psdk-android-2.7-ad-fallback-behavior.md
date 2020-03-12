---
description: Wenn Primetime und Decision eine VAST-Anzeige (kreativ) erzeugen, die leer ist oder einen Medientyp hat, der für HLS ungültig ist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.
seo-description: Wenn Primetime und Decision eine VAST-Anzeige (kreativ) erzeugen, die leer ist oder einen Medientyp hat, der für HLS ungültig ist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.
seo-title: Verhalten von Ad-Fallback für VAST und VMAP
title: Verhalten von Ad-Fallback für VAST und VMAP
uuid: 50e17372-fd29-4792-aafa-8f9c21cc42c6
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Verhalten von Ad-Fallback für VAST und VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wenn Primetime und Decision eine VAST-Anzeige (kreativ) erzeugen, die leer ist oder einen Medientyp hat, der für HLS ungültig ist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK ist der einzige gültige Medientyp `application/x-mpegURL` (M3U8).

Wenn es eigenständige Fallback-Anzeigen gibt, prüft das Primetime-Plug-in für Anzeigenentscheidungen diese Anzeigen in der folgenden Reihenfolge und gibt die erste Anzeige mit einem gültigen Medientyp zurück:

1. Wenn die Neuverpackung aktiviert ist, wird das erste Vorkommen einer Anzeige mit einem ungültigen Medientyp wie andere ungültige Medientypen behandelt.

   Wenn die Neuverpackung fehlschlägt, gilt dieser Vorgang für weitere Vorkommnisse der Anzeige.
1. Wenn TVSDK keine gültigen Fallback-Anzeigen findet, wird die ursprüngliche Anzeige mit dem ungültigen Medientyp zurückgegeben.
1. Wenn anstelle der ursprünglichen Anzeige eine Ausweichanzeige mit einem gültigen MIME-Typ zurückgegeben wird, sendet Primetime und Decision den Fehlercode 403 an die VAST-Fehler-URL, falls verfügbar.
1. Wenn eine Ausweichanzeige ein Wrapper ist und mehrere Anzeigen zurückgibt, werden nur Anzeigen mit dem richtigen Medientyp zurückgegeben.

>[!IMPORTANT]
>
>Dieses Verhalten ist immer für Anzeigen in VAST-Wrapper aktiviert. Bei Inline-Anzeigen von VAST in einem VMAP ist das Verhalten standardmäßig deaktiviert, aber Ihre Anwendung kann es aktivieren.

