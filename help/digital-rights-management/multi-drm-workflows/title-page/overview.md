---
description: Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mit der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen zählen FairPlay von Apple, Widevine von Google, PlayReady von Microsoft und Primetime Access von Adobe.
seo-description: Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mit der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen zählen FairPlay von Apple, Widevine von Google, PlayReady von Microsoft und Primetime Access von Adobe.
seo-title: Überblick über Multi-DRM
title: Überblick über Multi-DRM
uuid: 1705a338-baeb-4fcd-ae16-08963da55ab8
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Multi-DRM-Workflows {#multi-drm-workflows}

Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mit der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen zählen FairPlay von Apple, Widevine von Google, PlayReady von Microsoft und Primetime Access von Adobe.

## Überblick über Multi-DRM {#multi-drm-overview}

Adobe TVSDK unterstützt DRM-Schutz mit mehreren DRM-Schemata. Adobe Angebots *Primetime DRM Cloud, powered by ExpressPlay* , bietet Verpacken, Lizenzieren und Wiedergeben Ihrer Videoinhalte auf mehreren Plattformen.

Zu den unterstützten DRM-Schemata zählen das *Primetime Access* DRM (AAXS) von Adobe sowie native DRMs auf verschiedenen Geräten, einschließlich [Widevine](https://www.widevine.com) auf Chrome und Android, [FairPlay](https://developer.apple.com/streaming/fps/) auf Safari und iOS und [PlayReady](https://www.microsoft.com/playready/) auf Edge und XboxOne. Wenden Sie sich an einen Adobe-Kundenbetreuer, um Informationen darüber zu erhalten, welche DRM-Schemas derzeit auf diesen Plattformen verfügbar sind, sowie die geplanten Daten für zukünftige Versionen.

TVSDK unterstützt DRM-Lizenzen, die von jedem Lizenzserver unter Verwendung dieser Protokolle ausgestellt werden. Zusätzlich zur Unterstützung mehrerer DRM-Lösungen unterstützt Adobe Angebots *Primetime DRM Cloud mit ExpressPlay* als Lösung, bei der ExpressPlay die Lizenzserver für jede Lösung betreibt. Dadurch können Sie die Einrichtung und Wartung Ihrer DRM-Lizenz vereinfachen.

Um *Primetime DRM Cloud mit ExpressPlay* für die Implementierung Ihrer DRM-Anforderungen in TVSDK-Apps zu verwenden, müssen Sie zunächst ein [ExpressPlay.com](https://www.expressplay.com) -Konto erwerben. ExpressPlay bietet die Lizenzierungsfunktion für verschiedene DRM-Schutzsysteme und bietet auch andere Dienste wie Verpacken und Key Management an.

Ihr Adobe-Kundenbetreuer richtet zunächst Ihr ExpressPlay-Konto ein. Anschließend können Sie Ihr Konto konfigurieren und die *Kundenauthentifizierer* abrufen, die Sie bei Lizenztoken-Anfragen an die ExpressPlay-Server verwenden werden.