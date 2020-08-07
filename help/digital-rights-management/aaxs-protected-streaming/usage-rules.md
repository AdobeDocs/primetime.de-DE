---
seo-title: Nutzungsregeln
title: Nutzungsregeln
uuid: 361d07b9-e4c8-47ab-8c45-a1de98c9fed7
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
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
* Die Lizenzzwischenspeicherung ist standardmäßig deaktiviert. License caching can be enabled by specifying the caching end date or an amount of time caching is allowed (starting when the license is issued).
* Multiple Play Rights, which lets you specify different combinations of Output Protection, Application Restrictions, and DRM/Runtime Restrictions. For example, it is possible to specify different Output Protection requirements for each client platform by using the DRM Module Restriction with Output Protection.

>[!NOTE]
>
>To support remote key delivery to iOS devices, the policy used at packaging time must have remote key delivery enabled. Diese Einstellung kann nicht durch die Mandantenkonfiguration auf dem Server geändert werden. ***Adobe Primetime ist erforderlich, um iOS-Anwendungen zu erstellen, die Adobe Access-geschützte Inhalte wiedergeben können.***

