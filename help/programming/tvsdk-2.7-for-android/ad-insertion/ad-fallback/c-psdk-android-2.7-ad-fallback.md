---
description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
keywords: zero length ad;empty ad
seo-description: Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.
seo-title: Ad-Fallback für VAST- und VMAP-Anzeigen
title: Ad-Fallback für VAST- und VMAP-Anzeigen
uuid: ecfeff31-b723-4a0d-99f2-48705a37b5f0
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Übersicht {#ad-fallback-for-vast-and-vmap-ads-overview}

Für Anzeigen (oder kreative Anzeigen) mit digitaler Videoanzeigenserie (VAST), bei denen die Ausweichregel aktiviert ist, behandelt TVSDK eine Anzeige mit einem ungültigen Medientyp als leere Anzeige und versucht stattdessen Ausweichanzeigen zu verwenden. Sie können einige Aspekte des Ausweichverhaltens konfigurieren.

Die VAST/Digital Video Multiple Ad Playlist (VMAP)-Spezifikation besagt, dass bei Anzeigen, bei denen VAST-Fallback aktiviert ist, leere Anzeigen automatisch die Verwendung von Fallback-Anzeigen auslösen. Wenn eine VAST-Anzeige leer ist, sucht TVSDK nach einem gültigen HLS-Medientyp-Ersatz unter den Fallback-Anzeigen. Wenn eine VAST-Anzeige in einem Wrapper einen ungültigen Medientyp hat, behandelt TVSDK diese Anzeige als leer. Sie können konfigurieren, ob TVSDK dasselbe für Inline-Anzeigen in einem VMAP tun soll. Weitere Informationen zur Funktion VAST `fallbackOnNoAd` finden Sie unter [Vorlage für digitale Videoanzeige (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Nulllängenanzeigen** : Wenn TVSDK auf eine VAST-Antwort stößt, die eine Anzeige mit einer Dauer von null enthält, oder auf eine Werbeunterbrechung ohne Anzeigen, werden AD_BREAK_BEGINN/AD_BREAK_COMPLETE-Ereignis für diese unvollständigen Werbeunterbrechungen ausgelöst. *Dieses Verhalten gilt nur für VOD-Streams.* TVSDK löst diese Ereignis auch dann aus, wenn Ihre App die SKIP-Anzeigenrichtlinie verwendet.
>
>TVSDK löst *nicht* AD_BREAK_BEGINN/AD_BREAK_COMPLETE-Ereignis für Live-Streams aus, oder wenn ein Benutzer Trickplay verwendet oder versucht, über die Nulllänge-Anzeige hinauszugehen.

