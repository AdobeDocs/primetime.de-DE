---
title: Blockierungsliste der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt ausgeschlossen sind
description: Blockierungsliste der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt ausgeschlossen sind
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Blockierungsliste der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt ausgeschlossen sind {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

Gibt die Version von Primetime oder Flash Runtime an, die nicht auf Inhalte zugreifen kann. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Anwendungsbeispiel: Ähnlich wie bei der DRM-Client-Blockierungsliste kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als die Mindestversion angegeben werden, die für die Lizenzakquise und die Inhaltswiedergabe erforderlich ist.

Die Anwendungslaufzeit kann durch eines der Attribute identifiziert werden, die für DRM-Client-Versionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Gibt den Namen der Anwendungslaufzeit an. |
