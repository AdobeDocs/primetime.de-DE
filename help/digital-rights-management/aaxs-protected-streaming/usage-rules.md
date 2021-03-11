---
title: Nutzungsregeln
description: Nutzungsregeln
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Nutzungsregeln{#usage-rules}

Beim Adobe Access Server für geschütztes Streaming werden alle Nutzungsregeln über Konfigurationsdateien auf dem Server angegeben. Alle im geschützten Inhalt festgelegten Nutzungsregeln werden überschrieben. Daher wird empfohlen, beim Verpacken von Inhalten eine einfache anonyme Richtlinie zu verwenden. Benutzerregeln, die konfigurierbar sind, können pro Mandant festgelegt werden.

Adobe Access Server for Protected Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Einschränkungen für Adobe® AIR®-, SWF-, iOS- und Android-Anwendungen
* Einschränkungen für DRM- und Laufzeitmodule
* Durchsetzung der Jailbreak-Erkennung (auf Adobe Access-Plattformen, die die Erkennung von Jailbreak unterstützen)
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Die Lizenzzwischenspeicherung kann durch Angabe des Enddatums für die Zwischenspeicherung aktiviert werden, oder es ist eine zeitliche Zwischenspeicherung zulässig (beginnend mit der Lizenzerteilung).
* Rechte für mehrere Wiedergabe, mit denen Sie verschiedene Kombinationen aus Output Protection, Anwendungseinschränkungen und DRM-/Laufzeiteinschränkungen angeben können. Beispielsweise ist es möglich, mithilfe der DRM Module Restriction mit Output Protection unterschiedliche Ausgabeschutzanforderungen für jede Client-Plattform festzulegen.

>[!NOTE]
>
>Zur Unterstützung von Remote-Key-Versänden für iOS-Geräte muss der Remote-Key-Versand für die Richtlinie, die während der Paketerstellung verwendet wird, aktiviert sein. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die Adobe Access-geschützte Inhalte wiedergeben können.***

