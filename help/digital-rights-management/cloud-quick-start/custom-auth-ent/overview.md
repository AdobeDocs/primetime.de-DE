---
seo-title: BEES-Übersicht
title: BEES-Übersicht
uuid: c6ee7528-fdfa-4a56-bea2-a5e2dab6d428
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# BEES-Übersicht{#bees-overview}

Sie können einen Back-End-Berechtigungsdienst (BEES) implementieren, um benutzerdefinierte Berechtigungen für Ihren Primetime Cloud DRM-Vorgang bereitzustellen.

Primetime Cloud DRM verwendet standardmäßig den anonymen Versand der Lizenz. Das bedeutet, dass alle Lizenzanforderungen, die an Primetime Cloud DRM gesendet werden, eine gültige Lizenz zurückgeben, ohne zusätzliche Authentifizierung/Autorisierungsüberprüfungen durchzuführen (es sei denn, Sie haben eine Richtlinieneinschränkung angewendet, die die Verwendung der Adobe Primetime-Authentifizierung erfordert).

Der Lizenzantrag enthält die DRM-Richtlinie, die während der Verpackung/Verschlüsselung des Inhalts verwendet wurde. Die DRM-Richtlinie wird verwendet, um die DRM-Lizenz zu generieren, die an den Client zurückgegeben wird. Im Standardszenario müssen Sie alle DRM-Richtlinienentscheidungen zum Zeitpunkt der Inhaltspakete treffen. Kunden, die eine bessere Kontrolle über diese Workflows wünschen, haben folgende Optionen:

1. Integrieren Sie die Primetime-Authentifizierung, um vor der Wiedergabe zusätzliche Berechtigungsprüfungen hinzuzufügen.
1. Erstellen Sie einen lokalen Berechtigungsdienst, der von Primetime Cloud DRM Abfrage wird, bevor ein Gerät Inhalte wiedergeben kann, die Sie verpackt haben.

Ihr lokalen Berechtigungsdienst muss eine Antwort auf Primetime Cloud DRM bereitstellen, die die folgenden zwei Datenelemente enthält:

* `isAllowed`
* `drmPolicyToUse`

Diese bestimmen, ob ein Gerät den Inhalt abspielen darf und welche DRM-Richtlinie verwendet werden soll, um die DRM-Lizenz zu generieren (wenn `isAllowed` true ist).

In diesem Dokument wird beschrieben, was Sie tun müssen, um die oben genannte Option 2 zu erreichen: Implementieren Sie Ihren eigenen lokalen externen Berechtigungsdienst und stellen Sie ihn Primetime Cloud DRM für Inhalte bereit, die Sie verpackt haben.
