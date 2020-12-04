---
description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
seo-description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
seo-title: Ad-Fallback für VAST- und VMAP-Anzeigen
title: Ad-Fallback für VAST- und VMAP-Anzeigen
uuid: 7b44abf9-50cf-4e39-b594-ceb52208a865
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Ad Fallback für VAST- und VMAP-Anzeigen {#ad-fallback-for-vast-and-vmap-ads}

Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Die VAST/Digital Video Multiple Ad Playlist (VMAP)-Spezifikation besagt, dass bei Anzeigen, bei denen VAST-Fallback aktiviert ist, leere Anzeigen automatisch die Verwendung von Fallback-Anzeigen auslösen. Wenn eine VAST-Anzeige leer ist, sucht TVSDK nach einem gültigen HLS-Medientyp-Ersatz unter den Fallback-Anzeigen. Wenn eine VAST-Anzeige in einem Wrapper einen ungültigen Medientyp hat, behandelt TVSDK diese Anzeige als leer. Sie können konfigurieren, ob TVSDK dasselbe für Inline-Anzeigen in einem VMAP tun soll. Weitere Informationen zur Funktion VAST `fallbackOnNoAd` finden Sie unter [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

Das Primetime- und das Einfügeende-Back-End behalten eine Reihe von Prioritäten bei, damit es in derselben VAST/VMAP-Antwort zwischen verschiedenen Medientypen wählen kann. Weitere Informationen zu dieser Prioritätsstufe und zu ihrer Änderung finden Sie unter [Übersicht über CRS](../../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md).

## Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen {#define-fallback-ad-behavior-for-vmap-inline-ads}

Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.

1. Setzen Sie `fallbackOnInvalidCreative` auf &quot;true&quot;, damit VMAP zurückfällt, wenn der Medientyp für eine lineare/Inline-Anzeige für HLS ungültig ist.

   Der Standardwert ist false. Wenn eine lineare Anzeige fehlschlägt, weil sie einen ungültigen Medientyp hat oder weil die Anzeige nicht neu verpackt werden kann, erlaubt dieses Flag Primetime-Anzeigenentscheidung das gleiche Ausweichverhalten, als ob die Anzeige ein leerer VAST-Wrapper wäre.

   ```
   var auditudeMetadata:AuditudeSettings = new AuditudeSettings(); 
   auditudeMetadata.fallbackOnInvalidCreative = true;
   ```

## Ausweichverhalten von Anzeigen für VAST und VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wenn bei der Primetime-Anzeigenentscheidung eine VAST-Anzeige (kreatives Element) gefunden wird, die leer ist oder einen Medientyp hat, der für HLS ungültig ist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK sind die einzigen gültigen Medientypen `application/x-shockwave-flash` (VPAID) und `application/x-mpegURL` (m3u8).

Wenn es eigenständige Fallback-Anzeigen gibt, prüft das Primetime-Plugin für die Anzeigenentscheidung diese Anzeigen in der folgenden Reihenfolge und gibt die erste Anzeige mit einem gültigen Medientyp zurück:

1. Wenn die Neuverpackung aktiviert ist, wird das erste Vorkommen einer Anzeige mit einem ungültigen Medientyp wie andere ungültige Medientypen behandelt.

   Wenn die Neuverpackung fehlschlägt, gilt dieser Vorgang für weitere Vorkommnisse der Anzeige.
1. Wenn TVSDK keine gültigen Fallback-Anzeigen findet, wird die ursprüngliche Anzeige mit dem ungültigen Medientyp zurückgegeben.
1. Wenn anstelle der ursprünglichen Anzeige eine Ausweichanzeige mit einem gültigen MIME-Typ zurückgegeben wird, sendet die Primetime-Anzeigenentscheidung den Fehlercode 403 an die VAST-Fehler-URL, falls verfügbar.
1. Wenn eine Ausweichanzeige ein Wrapper ist und mehrere Anzeigen zurückgibt, werden nur Anzeigen mit dem richtigen Medientyp zurückgegeben.

>[!IMPORTANT]
>
>Dieses Verhalten ist immer für Anzeigen in VAST-Wrapper aktiviert. Bei Inline-Anzeigen von VAST in einem VMAP ist das Verhalten standardmäßig deaktiviert, aber Ihre Anwendung kann es aktivieren.