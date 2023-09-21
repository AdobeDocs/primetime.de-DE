---
description: Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mithilfe der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen gehören Apples FairPlay, Googles Widevine, Microsoft PlayReady und Primetime Access von Adobe.
title: Überblick über Multi-DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Multi-DRM-Workflows {#multi-drm-workflows}

Sie können mehrere DRM-Lösungen für Ihre TVSDK-Apps mithilfe der Primetime DRM Cloud, powered by ExpressPlay, implementieren. Zu den DRM-Lösungen gehören Apples FairPlay, Googles Widevine, Microsoft PlayReady und Primetime Access von Adobe.

## Überblick über Multi-DRM {#multi-drm-overview}

Adobe TVSDK unterstützt DRM-Schutz mit mehreren DRM-Schemata. Adobe-Angebote *Primetime DRM Cloud, powered by ExpressPlay* , um die Verpackung, Lizenzierung und Wiedergabe Ihres Videoinhalts auf mehreren Plattformen bereitzustellen.

Zu den unterstützten DRM-Schemata gehören Adobe *Primetime-Zugriff* DRM (AAXS) sowie native DRMs auf verschiedenen Geräten, darunter [Weitblickend](https://www.widevine.com) auf Chrome und Android, [FairPlay](https://developer.apple.com/streaming/fps/) in Safari und iOS und [PlayReady](https://www.microsoft.com/playready/) auf Edge und XboxOne. Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um Informationen darüber zu erhalten, welche DRM-Systeme derzeit auf diesen Plattformen verfügbar sind, sowie die geplanten Termine für zukünftige Versionen zu erhalten.

TVSDK unterstützt DRM-Lizenzen, die von jedem Lizenzserver unter Verwendung dieser Protokolle ausgestellt werden. Zusätzlich zur Unterstützung mehrerer DRM-Lösungen bietet Adobe *Primetime DRM Cloud, powered by ExpressPlay* als Lösung, in der ExpressPlay die Lizenzserver für jede Lösung betreibt. Dies kann die Einrichtung und Wartung für Ihre DRM-Lizenzerteilungsanforderungen vereinfachen.

Verwendung *Primetime DRM Cloud, powered by ExpressPlay* für die Implementierung Ihrer DRM-Anforderungen in TVSDK-Apps müssen Sie zunächst eine [ExpressPlay.com](https://www.expressplay.com) -Konto. ExpressPlay bietet die Lizenzierungsfunktion für verschiedene DRM-Schutzsysteme und bietet auch andere Dienste wie Verpackung und Schlüsselverwaltung an.

Ihr Adobe-Support-Mitarbeiter wird zunächst Ihr ExpressPlay-Konto einrichten. Anschließend können Sie Ihr Konto konfigurieren und den *Kundenauthentifikatoren* , die Sie in Lizenztoken-Anfragen an die ExpressPlay-Server verwenden werden.
