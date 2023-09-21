---
title: Blockierungsliste der Anwendungslaufzeiten
description: Blockierungsliste der Anwendungslaufzeiten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Blockierungsliste der Anwendungslaufzeiten {#blocklist-of-application-runtimes}

Blockierungsliste der Anwendungslaufzeiten gibt die Version des Primetime-Clients oder Flash Runtime an, die nicht auf Inhalte zugreifen kann. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Anwendungsbeispiel: Ähnlich wie bei der Primetime DRM Client-Blockierungsliste kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als die Mindestversion angegeben werden, die für die Lizenzakquise und die Inhaltswiedergabe erforderlich ist.

Sie können die Anwendungslaufzeit anhand eines der Attribute identifizieren, die für die Primetime DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exakte Übereinstimmung | Gibt den Namen der Anwendungslaufzeit an. |
