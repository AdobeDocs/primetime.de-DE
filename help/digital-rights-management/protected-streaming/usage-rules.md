---
description: Mit Adobe Primetime DRM Server for Protected Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
seo-description: Mit Adobe Primetime DRM Server for Protected Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
seo-title: Verwendungsregeln
title: Verwendungsregeln
uuid: 4a794712-db58-43f5-b867-8871e58e12ae
translation-type: tm+mt
source-git-commit: 68f1318db89cf9422f5969f669c11f3784560db6

---


# Verwendungsregeln{#about-usage-rules}

Mit Adobe Primetime DRM Server for Protected Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.

Alle in der DRM-Richtlinie für den geschützten Inhalt angegebenen Verwendungsregeln werden überschrieben. Daher empfiehlt Adobe, dass Sie während der Inhaltspakete eine einfache, anonyme DRM-Richtlinie verwenden. Alle von Ihnen konfigurierten Nutzungsregeln können pro Mandant konfiguriert werden.

Der Primetime-DRM-Server für geschütztes Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Adobe® AIR®-, SWF-, iOS- und Android-Anwendungsbeschränkungen
* Einschränkungen für DRM- und Laufzeitmodule
* Durchsetzung der Jailbreak-Erkennung auf Primetime-DRM-Plattformen, die die Erkennung von Jailbreak unterstützen
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Die Zwischenspeicherung von Lizenzen, die Sie aktivieren können, indem Sie das Enddatum der Zwischenspeicherung angeben oder eine Zeitzwischenspeicherung festlegen, ist zulässig. es Beginn bei Erteilung der Lizenz.
* Rechte für mehrere Wiedergabe, mit denen Sie verschiedene Kombinationen aus Output Protection, Anwendungseinschränkungen und DRM-/Laufzeiteinschränkungen angeben können. Beispielsweise können Sie mithilfe der DRM-Modulbeschränkung mit Output Protection für jede Clientplattform unterschiedliche Ausgabeschutzanforderungen festlegen.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Wenn Sie Remote-Key-Versand auf iOS-Geräten unterstützen möchten, muss der Remote-Key-Versand für die DRM-Richtlinie, die zur Verpackungszeit angewendet wird, aktiviert sein. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden.

