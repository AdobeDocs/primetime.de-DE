---
description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
keywords: zero length ad;empty ad
seo-description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
seo-title: Ad-Fallback für VAST- und VMAP-Anzeigen
title: Ad-Fallback für VAST- und VMAP-Anzeigen
uuid: 688f0b67-9f5b-4c21-ab33-86d21580fbe9
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Ad Fallback für VAST- und VMAP-Anzeigen {#ad-fallback-for-vast-and-vmap-ads}

Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Die VAST/Digital Video Multiple Ad Playlist (VMAP)-Spezifikation besagt, dass bei Anzeigen, bei denen VAST-Fallback aktiviert ist, leere Anzeigen automatisch die Verwendung von Fallback-Anzeigen auslösen. Wenn eine VAST-Anzeige leer ist, sucht TVSDK nach einem gültigen HLS-Medientyp-Ersatz unter den Fallback-Anzeigen. Wenn eine VAST-Anzeige in einem Wrapper einen ungültigen Medientyp hat, behandelt TVSDK diese Anzeige als leer. Sie können konfigurieren, ob TVSDK dasselbe für Inline-Anzeigen in einem VMAP tun soll. Weitere Informationen zur Funktion VAST `fallbackOnNoAd` finden Sie unter [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Nulllängenanzeigen** : Wenn TVSDK auf eine VAST-Antwort stößt, die eine Anzeige mit einer Dauer von null enthält, oder auf eine Werbeunterbrechung ohne Anzeigen, werden AD_BREAK_BEGINN/AD_BREAK_COMPLETE-Ereignis für diese unvollständigen Werbeunterbrechungen ausgelöst. *Dieses Verhalten gilt nur für VOD-Streams.* TVSDK löst diese Ereignis auch dann aus, wenn Ihre App die SKIP-Anzeigenrichtlinie verwendet.
>
>TVSDK löst *nicht* AD_BREAK_BEGINN/AD_BREAK_COMPLETE-Ereignis für Live-Streams aus, oder wenn ein Benutzer Trickplay verwendet oder versucht, über die Nulllänge-Anzeige hinauszugehen.