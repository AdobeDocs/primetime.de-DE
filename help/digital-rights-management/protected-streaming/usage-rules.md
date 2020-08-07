---
description: Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
seo-description: Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
seo-title: Verwendungsregeln
title: Verwendungsregeln
uuid: 4a794712-db58-43f5-b867-8871e58e12ae
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Verwendungsregeln{#about-usage-rules}

Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.

Alle in der DRM-Richtlinie für den geschützten Inhalt angegebenen Verwendungsregeln werden überschrieben. Daher empfiehlt Adobe, während der Inhaltspakete eine einfache, anonyme DRM-Richtlinie zu verwenden. Alle von Ihnen konfigurierten Nutzungsregeln können pro Mandant konfiguriert werden.

The Primetime DRM Server for Protected Streaming supports the following usage rules:

* Output Protection
* Adobe® AIR®, SWF, iOS, and Android Application Restrictions
* DRM and Runtime Module Restrictions
* Durchsetzung der Jailbreak-Erkennung auf Primetime-DRM-Plattformen, die die Erkennung von Jailbreak unterstützen
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Die Zwischenspeicherung von Lizenzen, die Sie aktivieren können, indem Sie das Enddatum der Zwischenspeicherung angeben oder eine Zeitzwischenspeicherung festlegen, ist zulässig. es Beginn bei Erteilung der Lizenz.
* Multiple Play Rights that let you specify different combinations of Output Protection, Application Restrictions, and DRM/Runtime Restrictions. Beispielsweise können Sie mithilfe der DRM-Modulbeschränkung mit Output Protection für jede Clientplattform unterschiedliche Ausgabeschutzanforderungen festlegen.

>[!NOTE]
>
>If you want to support remote key delivery to iOS devices, then the DRM policy that is applied at packaging time must have remote key delivery enabled. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden.

