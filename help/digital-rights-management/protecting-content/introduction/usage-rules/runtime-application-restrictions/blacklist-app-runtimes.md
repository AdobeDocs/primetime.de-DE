---
description: 'null'
seo-description: 'null'
seo-title: Blacklist of application runtimes
title: Blacklist of application runtimes
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Blacklist of application runtimes{#blacklist-of-application-runtimes}

Die Blacklist der Anwendungs-Laufzeitumgebungen gibt die Version des Primetime-Clients oder der Flash-Laufzeitumgebung an, die keinen Zugriff auf Inhalte hat. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der Blacklist Primetime DRM Client kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als die Mindestanforderung für die Lizenzerfassung und Inhaltswiedergabe angegeben werden.

Sie können die Anwendungslaufzeit anhand eines der Attribute identifizieren, die für Primetime DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |

