---
seo-title: Nutzungsregeln
title: Nutzungsregeln
uuid: 361d07b9-e4c8-47ab-8c45-a1de98c9fed7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Nutzungsregeln{#usage-rules}

Beim Adobe Access Server für geschütztes Streaming werden alle Nutzungsregeln über Konfigurationsdateien auf dem Server angegeben. Alle im geschützten Inhalt festgelegten Nutzungsregeln werden überschrieben. Daher wird empfohlen, beim Verpacken von Inhalten eine einfache anonyme Richtlinie zu verwenden. Benutzerregeln, die konfigurierbar sind, können pro Mandant festgelegt werden.

Adobe Access Server for Protected Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Adobe® AIR®-, SWF-, iOS- und Android-Anwendungsbeschränkungen
* Einschränkungen für DRM- und Laufzeitmodule
* Durchsetzung der Jailbreak-Erkennung (auf Adobe Access-Plattformen, die die Erkennung von Jailbreak unterstützen)
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Die Lizenzzwischenspeicherung kann durch Angabe des Enddatums für die Zwischenspeicherung aktiviert werden, oder es ist eine zeitliche Zwischenspeicherung zulässig (beginnend mit der Lizenzerteilung).
* Rechte für mehrere Wiedergabe, mit denen Sie verschiedene Kombinationen aus Output Protection, Anwendungseinschränkungen und DRM-/Laufzeiteinschränkungen angeben können. Beispielsweise ist es möglich, mithilfe der DRM Module Restriction mit Output Protection unterschiedliche Ausgabeschutzanforderungen für jede Client-Plattform festzulegen.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Zur Unterstützung von Remote-Key-Versänden für iOS-Geräte muss der Remote-Key-Versand für die Richtlinie, die während der Paketerstellung verwendet wird, aktiviert sein. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die Adobe Access-geschützte Inhalte wiedergeben können.***

