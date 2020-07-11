---
seo-title: Blockierungsliste von Anwendungslaufzeiten, die den Zugriff auf geschützten Inhalt einschränken
title: Blockierungsliste von Anwendungslaufzeiten, die den Zugriff auf geschützten Inhalt einschränken
uuid: 462a2c09-b335-4768-bd0e-1359db169d69
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Blockierungsliste von Anwendungslaufzeiten, die den Zugriff auf geschützten Inhalt einschränken {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

Gibt die Version der Primetime- oder Flash-Laufzeitumgebung an, auf die kein Zugriff auf Inhalte möglich ist. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der DRM-Client-Blockierungsliste kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als Mindestversion für die Lizenzerfassung und Inhaltswiedergabe angegeben werden.

Die Anwendungslaufzeit kann durch eines der Attribute identifiziert werden, die für DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |
