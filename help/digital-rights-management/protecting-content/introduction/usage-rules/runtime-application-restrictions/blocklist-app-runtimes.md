---
description: 'null'
seo-description: 'null'
seo-title: Blockierungsliste der Anwendungslaufzeiten
title: Blockierungsliste der Anwendungslaufzeiten
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Blockierungsliste der Anwendungslaufzeiten{#blocklist-of-application-runtimes}

Die Blockierungsliste der Anwendungs-Laufzeitumgebungen gibt die Version des Primetime-Clients oder der Flash-Laufzeitumgebung an, auf die kein Zugriff auf Inhalte möglich ist. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der Primetime DRM Client-blockierungsliste kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden.

Sie können die Anwendungslaufzeit anhand eines der Attribute identifizieren, die für Primetime DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |

