---
description: Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mit der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen zählen FairPlay von Apple, Widevine von Google, PlayReady von Microsoft und Primetime Access von der Adobe.
title: Überblick über Multi-DRM
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Multi-DRM Workflows {#multi-drm-workflows}

Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mit der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen zählen FairPlay von Apple, Widevine von Google, PlayReady von Microsoft und Primetime Access von der Adobe.

## Überblick über Multi-DRM {#multi-drm-overview}

Adobe TVSDK unterstützt DRM-Schutz mit mehreren DRM-Schemata. Adobe-Angebot *Primetime DRM Cloud, powered by ExpressPlay*, um Verpacken, Lizenzieren und Wiedergeben Ihrer Videoinhalte auf mehreren Plattformen bereitzustellen.

Zu den unterstützten DRM-Schemata gehören die DRM-Adobe *Primetime Access* DRM (AAXS) sowie native DRMs auf verschiedenen Geräten, einschließlich [Widevine](https://www.widevine.com) auf Chrome und Android, [FairPlay](https://developer.apple.com/streaming/fps/) auf Safari und iOS und [PlayReady](https://www.microsoft.com/playready/) Edge und XboxOne. Wenden Sie sich an einen Kundenbetreuer, um Informationen darüber zu erhalten, welche DRM-Programme derzeit auf diesen Plattformen verfügbar sind und zu welchen Terminen zukünftige Versionen geplant sind.

TVSDK unterstützt DRM-Lizenzen, die von jedem Lizenzserver unter Verwendung dieser Protokolle ausgestellt werden. Zusätzlich zur Unterstützung mehrerer DRM-Lösungen bieten Adobe-Angebot *Primetime DRM Cloud, powered by ExpressPlay* als Lösung, in der ExpressPlay die Lizenzserver für jede Lösung betreibt. Dadurch können Sie die Einrichtung und Wartung Ihrer DRM-Lizenz vereinfachen.

Um *Primetime DRM Cloud, powered by ExpressPlay* zur Implementierung Ihrer DRM-Anforderungen in TVSDK-Apps zu verwenden, müssen Sie zunächst ein [ExpressPlay.com](https://www.expressplay.com)-Konto abrufen. ExpressPlay bietet die Lizenzierungsfunktion für verschiedene DRM-Schutzsysteme sowie weitere Dienste wie Verpackung und Key Management.

Ihr Kundenbetreuer richtet zunächst Ihr ExpressPlay-Konto ein. Anschließend können Sie Ihr Konto konfigurieren und die *Kundenauthentifizierer* abrufen, die Sie bei Lizenztoken-Anfragen an die ExpressPlay-Server verwenden werden.