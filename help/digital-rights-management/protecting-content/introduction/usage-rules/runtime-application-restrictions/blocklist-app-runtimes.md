---
title: Blockierungsliste der Anwendungslaufzeiten
description: Blockierungsliste der Anwendungslaufzeiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Blockierungsliste der Anwendungslaufzeiten {#blocklist-of-application-runtimes}

Die Blockierungsliste der Anwendungs-Laufzeitumgebungen gibt die Version des Primetime-Clients oder der Flash-Laufzeit an, die keinen Zugriff auf Inhalte hat. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der Primetime DRM Client-Blockierungsliste kann auch die neueste Version des Flash Players, der AIR- oder iOS-Laufzeitumgebungen als die Mindestversion angegeben werden, die für die Lizenzerfassung und Inhaltswiedergabe erforderlich ist.

Sie können die Anwendungslaufzeit anhand eines der Attribute identifizieren, die für Primetime DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |

