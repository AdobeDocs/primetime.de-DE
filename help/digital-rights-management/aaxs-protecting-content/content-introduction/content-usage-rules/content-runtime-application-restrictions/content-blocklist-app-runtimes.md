---
title: Blockierungsliste von Anwendungslaufzeiten, die den Zugriff auf geschützten Inhalt einschränken
description: Blockierungsliste von Anwendungslaufzeiten, die den Zugriff auf geschützten Inhalt einschränken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Blockierungsliste von Anwendungs-Laufzeitumgebungen, die vom Zugriff auf geschützten Inhalt eingeschränkt sind{#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

Gibt die Primetime- oder Flash-Laufzeitversion an, die keinen Zugriff auf Inhalte hat. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der DRM-Client-Blockierungsliste kann auch die neueste Version des Flash Players, der AIR- oder iOS-Laufzeitumgebungen als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden.

Die Anwendungslaufzeit kann durch eines der Attribute identifiziert werden, die für DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |
