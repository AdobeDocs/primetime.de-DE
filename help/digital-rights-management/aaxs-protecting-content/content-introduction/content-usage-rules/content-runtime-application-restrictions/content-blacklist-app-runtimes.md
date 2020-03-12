---
seo-title: Blacklist der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt eingeschränkt sind
title: Blacklist der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt eingeschränkt sind
uuid: 462a2c09-b335-4768-bd0e-1359db169d69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Blacklist der Anwendungslaufzeiten, die vom Zugriff auf geschützten Inhalt eingeschränkt sind {#blacklist-of-application-runtimes-restricted-from-accessing-protected-content}

Gibt die Version der Primetime- oder Flash-Laufzeitumgebung an, auf die kein Zugriff auf Inhalte möglich ist. Geben Sie die eingeschränkte Laufzeit (Flash Player, AIR oder iOS), Plattform und Version an.

Verwendungsbeispiel: Ähnlich wie bei der Blacklist des DRM-Clients kann auch die neueste Version der Flash Player-, AIR- oder iOS-Laufzeitumgebungen als die Mindestanforderung für die Lizenzerfassung und Inhaltswiedergabe angegeben werden.

Die Anwendungslaufzeit kann durch eines der Attribute identifiziert werden, die für DRM-Clientversionen unterstützt werden, zusätzlich zu den folgenden Attributen:

| **Attribut** | **Unterstützte Werte** | **Übereinstimmungskriterien** | **Beschreibung** |
|---|---|---|---|
| Anwendung | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Exakte Übereinstimmung | Identifiziert den Namen der Anwendungslaufzeit. |

