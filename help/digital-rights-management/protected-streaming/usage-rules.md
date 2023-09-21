---
description: Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
title: Über Nutzungsregeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Über Nutzungsregeln{#about-usage-rules}

Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.

Alle in der DRM-Richtlinie für den geschützten Inhalt angegebenen Nutzungsregeln werden überschrieben. Daher empfiehlt Adobe, eine einfache, anonyme DRM-Richtlinie während der Inhaltspackung zu verwenden. Alle Nutzungsregeln, die Sie konfigurieren können, können pro Mandant konfiguriert werden.

Der Primetime-DRM-Server für geschütztes Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Anwendungsbeschränkungen für Adobe® AIR®, SWF, iOS und Android
* DRM- und Laufzeitmodulbeschränkungen
* Durchsetzung der Jailbreak-Erkennung auf Primetime-DRM-Plattformen, die die Erkennung von Jailbreak unterstützen
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Lizenzzwischenspeicherung, die Sie aktivieren können, indem Sie das Enddatum für die Zwischenspeicherung angeben oder eine zeitliche Zwischenspeicherung zulässig ist. Sie beginnt mit der Erteilung der Lizenz.
* Mehrere Wiedergabeberechtigungen , mit denen Sie verschiedene Kombinationen aus Output Protection, Application Restrictions und DRM/Runtime Restrictions festlegen können. Beispielsweise können Sie mithilfe der DRM-Modulbeschränkung mit Output Protection verschiedene Output Protection-Anforderungen für jede Client-Plattform angeben.

>[!NOTE]
>
>Wenn Sie die Bereitstellung von Remote-Schlüsseln auf iOS-Geräten unterstützen möchten, muss die Bereitstellung von Remote-Schlüsseln für die DRM-Richtlinie, die beim Verpacken angewendet wird, aktiviert sein. Diese Einstellung kann nicht über die Mandantenkonfiguration auf dem Server geändert werden.
