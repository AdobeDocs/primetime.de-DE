---
description: Wenn Primetime und Decisioning eine VAST-Anzeige (kreativ) aufrufen, die leer ist oder einen für HLS ungültigen Medientyp aufweist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.
title: Ausweichverhalten von Anzeigen für VAST und VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Ausweichverhalten von Anzeigen für VAST und VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wenn Primetime und Decisioning eine VAST-Anzeige (kreativ) aufrufen, die leer ist oder einen für HLS ungültigen Medientyp aufweist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK lautet der einzige gültige Medientyp `application/x-mpegURL` (M3U8).

Wenn es eigenständige Fallback-Anzeigen gibt, prüft das Primetime-Anzeigen-Entscheidungs-Plug-in diese Anzeigen in der folgenden Reihenfolge und gibt die erste Anzeige mit einem gültigen Medientyp zurück:

1. Wenn die Neuverpackung aktiviert ist, wird das erste Auftreten einer Anzeige mit einem ungültigen Medientyp wie andere ungültige Medientypen behandelt.

   Wenn die Neuverpackung fehlschlägt, gilt dieser Prozess für zusätzliche Vorkommen der Anzeige.
1. Wenn TVSDK keine gültigen Fallback-Anzeigen findet, wird die ursprüngliche Anzeige mit dem ungültigen Medientyp zurückgegeben.
1. Wenn anstelle der ursprünglichen Anzeige eine Fallback-Anzeige mit einem gültigen MIME-Typ zurückgegeben wird, sendet Primetime-Anzeigenentscheidung den Fehlercode 403 an die VAST-Fehler-URL, sofern verfügbar.
1. Wenn eine Fallback-Anzeige ein Wrapper ist und mehrere Anzeigen zurückgibt, werden nur Anzeigen mit dem richtigen Medientyp zurückgegeben.

>[!IMPORTANT]
>
>Dieses Verhalten ist immer für Anzeigen in VAST-Wrappern aktiviert. Für VAST-Anzeigen inline in einem VMAP ist das Verhalten standardmäßig deaktiviert, aber Ihre Anwendung kann es aktivieren.
