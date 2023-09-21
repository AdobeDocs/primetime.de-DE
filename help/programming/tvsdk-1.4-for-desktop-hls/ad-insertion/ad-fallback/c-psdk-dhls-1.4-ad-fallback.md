---
description: Bei Anzeigen (oder kreativen Werbevorlagen) mit aktivierter Ausweichregel für digitale Videoanzeigen behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen, Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
title: Anzeigen-Fallback für VAST- und VMAP-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Anzeigen-Fallback für VAST- und VMAP-Anzeigen {#ad-fallback-for-vast-and-vmap-ads}

Bei Anzeigen (oder kreativen Werbevorlagen) mit aktivierter Ausweichregel für digitale Videoanzeigen behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen, Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

In der VAST/Digital Video Multiple Ad Play List (VMAP)-Spezifikation ist festgelegt, dass bei Anzeigen, bei denen VAST-Fallback aktiviert ist, bei leeren Anzeigen automatisch der Trigger der Verwendung von Fallback-Anzeigen erfolgt. Wenn eine VAST-Anzeige leer ist, sucht TVSDK unter den Fallback-Anzeigen nach einem gültigen HLS-Medientyp-Ersatz. Wenn eine VAST-Anzeige in einem Wrapper einen ungültigen Medientyp aufweist, behandelt TVSDK diese Anzeige als leer. Sie können konfigurieren, ob TVSDK für inline-Anzeigen in einem VMAP dasselbe tun soll. Weitere Informationen zum VAST `fallbackOnNoAd` -Funktion, siehe [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## Definieren des Fallback-Anzeigenverhaltens für VMAP-Inline-Anzeigen {#define-fallback-ad-behavior-for-vmap-inline-ads}

Sie können die Ausweichmöglichkeit aktivieren, wenn eine VMAP-Inline-Anzeige einen ungültigen Medientyp enthält.

1. Satz `fallbackOnInvalidCreative` auf &quot;true&quot;, damit VMAP zurückgesetzt wird, wenn der Medientyp für eine lineare/Inline-Anzeige für HLS ungültig ist.

   Der Standardwert ist false. Wenn eine lineare Anzeige fehlschlägt, weil sie einen ungültigen Medientyp aufweist oder weil die Anzeige nicht neu verpackt werden kann, ermöglicht dieses Flag, dass die Primetime-Anzeigenentscheidung dasselbe Ausweichverhalten wie ein leerer VAST-Wrapper anwendet.

   ```
   var auditudeMetadata:AuditudeSettings = new AuditudeSettings(); 
   auditudeMetadata.fallbackOnInvalidCreative = true;
   ```

## Ausweichverhalten von Anzeigen für VAST und VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wenn bei der Primetime-Anzeigenentscheidung eine leere VAST-Anzeige (kreatives Element) auftritt oder der Medientyp ungültig für HLS ist, werden die Fallback-Anzeigen ausgewertet, um zu bestimmen, was zurückgegeben werden soll.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK sind die einzigen gültigen Medientypen `application/x-shockwave-flash` (VPAID) und `application/x-mpegURL` (m3u8).

Wenn es eigenständige Fallback-Anzeigen gibt, prüft das Primetime-Anzeigen-Decisioning-Plug-in diese Anzeigen in der folgenden Reihenfolge und gibt die erste Anzeige mit einem gültigen Medientyp zurück:

1. Wenn die Neuverpackung aktiviert ist, wird das erste Auftreten einer Anzeige mit einem ungültigen Medientyp wie andere ungültige Medientypen behandelt.

   Wenn die Neuverpackung fehlschlägt, gilt dieser Prozess für zusätzliche Vorkommen der Anzeige.
1. Wenn TVSDK keine gültigen Fallback-Anzeigen findet, wird die ursprüngliche Anzeige mit dem ungültigen Medientyp zurückgegeben.
1. Wenn anstelle der ursprünglichen Anzeige eine Fallback-Anzeige mit einem gültigen MIME-Typ zurückgegeben wird, sendet Primetime Ad Decisioning den Fehlercode 403 an die VAST-Fehler-URL, sofern verfügbar.
1. Wenn eine Fallback-Anzeige ein Wrapper ist und mehrere Anzeigen zurückgibt, werden nur Anzeigen mit dem richtigen Medientyp zurückgegeben.

>[!IMPORTANT]
>
>Dieses Verhalten ist immer für Anzeigen in VAST-Wrappern aktiviert. Für VAST-Anzeigen inline in einem VMAP ist das Verhalten standardmäßig deaktiviert, aber Ihre Anwendung kann es aktivieren.
