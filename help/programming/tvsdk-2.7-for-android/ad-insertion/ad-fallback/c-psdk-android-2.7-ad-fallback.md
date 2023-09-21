---
description: Bei Anzeigen (oder kreativen Werbevorlagen) mit aktivierter Ausweichregel für digitale Videoanzeigen behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen, Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
keywords: Anzeige mit Nulllänge; leere Anzeige
title: Anzeigen-Fallback für VAST- und VMAP-Anzeigen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Übersicht {#ad-fallback-for-vast-and-vmap-ads-overview}

Bei Anzeigen (oder kreativen Werbevorlagen) mit aktivierter Ausweichregel für digitale Videoanzeigen behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen, Fallback-Anzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Die Spezifikation VAST/Digital Video Multiple Ad Play List (VMAP) besagt, dass bei Anzeigen mit aktiviertem VAST-Fallback bei leeren Anzeigen automatisch die Verwendung von Fallback-Anzeigen Trigger wird. Wenn eine VAST-Anzeige leer ist, sucht TVSDK unter den Fallback-Anzeigen nach einem gültigen HLS-Medientyp-Ersatz. Wenn eine VAST-Anzeige in einem Wrapper einen ungültigen Medientyp aufweist, behandelt TVSDK diese Anzeige als leer. Sie können konfigurieren, ob TVSDK für inline-Anzeigen in einem VMAP dasselbe tun soll. Weitere Informationen zum VAST `fallbackOnNoAd` -Funktion, siehe [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Null Längenanzeigen** - Wenn TVSDK auf eine VAST-Antwort stößt, die eine Anzeige von null Dauer enthält, oder auf eine Werbeunterbrechung ohne Anzeigen, werden AD_BREAK_START / AD_BREAK_COMPLETE-Ereignisse für diese Werbeunterbrechungen mit null Länge ausgelöst. *Dieses Verhalten gilt nur für VOD-Streams.* TVSDK löst diese Ereignisse auch dann aus, wenn Ihre App die SKIP-Anzeigenrichtlinie verwendet.
>
>TVSDK *not* Auslösen von AD_BREAK_START / AD_BREAK_COMPLETE-Ereignissen für Live-Streams oder wenn ein Benutzer Trickplay verwendet oder versucht, die Anzeige mit einer Länge von null zu überspringen.
