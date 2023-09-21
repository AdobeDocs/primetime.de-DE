---
title: Nutzungsregeln
description: Nutzungsregeln
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Nutzungsregeln{#usage-rules}

Mit Adobe Access Server für geschütztes Streaming werden alle Nutzungsregeln über Konfigurationsdateien auf dem Server angegeben. Sämtliche im geschützten Inhalt festgelegten Nutzungsregeln werden überschrieben. Daher wird empfohlen, bei der Inhaltspakete eine einfache anonyme Richtlinie zu verwenden. konfigurierbare Nutzungsregeln können pro Mandant festgelegt werden.

Adobe Access Server für geschütztes Streaming unterstützt die folgenden Nutzungsregeln:

* Output Protection
* Anwendungsbeschränkungen für Adobe® AIR®, SWF, iOS und Android
* DRM- und Laufzeitmodulbeschränkungen
* Durchsetzung der Jailbreak-Erkennung (auf Adobe Access-Plattformen, die die Jailbreak-Erkennung unterstützen)
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. Lizenzzwischenspeicherung kann durch Angabe des Enddatums für die Zwischenspeicherung aktiviert werden. Andernfalls ist eine zeitliche Zwischenspeicherung zulässig (beginnend mit der Lizenzerteilung).
* Mehrere Wiedergabeberechtigungen, mit denen Sie verschiedene Kombinationen aus Output Protection, Application Restrictions und DRM/Runtime Restrictions angeben können. Beispielsweise ist es möglich, mithilfe der DRM Module Restriction mit Output Protection verschiedene Output Protection-Anforderungen für jede Client-Plattform anzugeben.

>[!NOTE]
>
>Um die Bereitstellung von Remote-Schlüsseln auf iOS-Geräten zu unterstützen, muss die Bereitstellung von Remote-Schlüsseln für die bei der Paketierung verwendete Richtlinie aktiviert sein. Diese Einstellung kann nicht über die Mandantenkonfiguration auf dem Server geändert werden. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die Adobe-zugriffsgeschützte Inhalte wiedergeben können.***
