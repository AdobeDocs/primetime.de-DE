---
title: BEES-Übersicht
description: BEES-Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# BEES-Übersicht{#bees-overview}

Sie können einen Back-End-Berechtigungsdienst (BEES) implementieren, um benutzerdefinierte Berechtigungen für Ihren Primetime Cloud DRM-Vorgang bereitzustellen.

Primetime Cloud DRM verwendet standardmäßig die anonyme Lizenzbereitstellung. Das bedeutet, dass alle an Primetime Cloud DRM gesendeten Lizenzanfragen eine gültige Lizenz zurückgeben, ohne dass zusätzliche Authentifizierungs-/Autorisierungsüberprüfungen durchgeführt werden (es sei denn, Sie haben eine Richtlinienbeschränkung angewendet, die die Adobe Primetime-Authentifizierung erfordert).

Der Lizenzantrag enthält die DRM-Richtlinie, die während der Verpackung/Verschlüsselung des Inhalts verwendet wurde. Die DRM-Richtlinie wird verwendet, um die DRM-Lizenz zu generieren, die an den Client zurückgegeben wird. Im Standardszenario müssen Sie alle DRM-Richtlinienentscheidungen zum Zeitpunkt der Inhaltserstellung treffen. Kunden, die eine bessere Kontrolle über diese Workflows wünschen, haben die folgenden Optionen:

1. Integrieren Sie die Primetime-Authentifizierung, um vor der Wiedergabe zusätzliche Berechtigungsprüfungen hinzuzufügen.
1. Erstellen Sie einen lokalen Berechtigungsdienst, den Primetime Cloud DRM abfragen wird, bevor Sie einem Gerät die Wiedergabe von gepackten Inhalten ermöglichen.

Ihr lokaler Berechtigungsdienst muss eine Antwort an Primetime Cloud DRM bereitstellen, die die beiden folgenden Daten enthält:

* `isAllowed`
* `drmPolicyToUse`

Diese bestimmen, ob ein Gerät den Inhalt wiedergeben darf und welche DRM-Richtlinie zum Generieren der DRM-Lizenz verwendet werden soll (wenn `isAllowed` ist wahr).

In diesem Dokument wird beschrieben, was Sie tun müssen, um Option 2 oben auszuführen: Implementieren Sie Ihren eigenen lokalen externen Berechtigungsdienst und stellen Sie ihn Primetime Cloud DRM für Inhalte zur Verfügung, die Sie verpackt haben.
