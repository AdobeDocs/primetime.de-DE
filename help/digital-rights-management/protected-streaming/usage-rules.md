---
description: Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.
title: Verwendungsregeln
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# Informationen zu Verwendungsregeln{#about-usage-rules}

Mit dem Adobe Primetime DRM-Server für geschütztes Streaming können Sie alle Nutzungsregeln auf dem Server mit Konfigurationsdateien angeben.

Alle in der DRM-Richtlinie für den geschützten Inhalt angegebenen Verwendungsregeln werden überschrieben. Daher empfiehlt Adobe, während der Inhaltspakete eine einfache, anonyme DRM-Richtlinie zu verwenden. Alle von Ihnen konfigurierten Nutzungsregeln können pro Mandant konfiguriert werden.

Der Primetime-DRM-Server für geschütztes Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Einschränkungen für Adobe® AIR®-, SWF-, iOS- und Android-Anwendungen
* Einschränkungen für DRM- und Laufzeitmodule
* Durchsetzung der Jailbreak-Erkennung auf Primetime-DRM-Plattformen, die die Erkennung von Jailbreak unterstützen
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Die Zwischenspeicherung von Lizenzen, die Sie aktivieren können, indem Sie das Enddatum der Zwischenspeicherung angeben oder eine Zeitzwischenspeicherung festlegen, ist zulässig. es Beginn bei Erteilung der Lizenz.
* Rechte für mehrere Wiedergabe, mit denen Sie verschiedene Kombinationen aus Output Protection, Anwendungseinschränkungen und DRM-/Laufzeiteinschränkungen angeben können. Beispielsweise können Sie mithilfe der DRM-Modulbeschränkung mit Output Protection für jede Clientplattform unterschiedliche Ausgabeschutzanforderungen festlegen.

>[!NOTE]
>
>Wenn Sie Remote-Key-Versand auf iOS-Geräten unterstützen möchten, muss der Remote-Key-Versand für die DRM-Richtlinie, die zur Verpackungszeit angewendet wird, aktiviert sein. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden.

