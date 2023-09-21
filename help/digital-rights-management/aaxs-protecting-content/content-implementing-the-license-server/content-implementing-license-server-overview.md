---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Übersicht{#overview}

Um Lizenzen für Clients zu erteilen, müssen Sie einen Adobe Access-Lizenzserver bereitstellen. Der Lizenzserver verwendet das Adobe® Access™ SDK, um die folgenden Aufgaben auszuführen:

* Verarbeiten Sie Authentifizierungsanfragen, wenn die Authentifizierung mit Benutzername/Kennwort unterstützt wird.
* Lizenzanforderungen bearbeiten
* Verarbeitung von Server-Versionsanfragen - Alle Server müssen Unterstützung für diesen Anforderungstyp implementieren.
* Registrierungsanfragen für Domänen verarbeiten - nur bei Implementierung eines Domänenservers erforderlich.
* Domänenderegistrierungsanfragen verarbeiten - nur bei Implementierung eines Domänenservers erforderlich.
* Synchronisation von Prozessen - nur erforderlich, wenn Lizenzen die Synchronisierungsanforderungen angeben.

Darüber hinaus muss der Server Geschäftslogik für die Authentifizierung von Benutzern bereitstellen, um zu bestimmen, ob Benutzer berechtigt sind, Inhalte anzuzeigen und optional die Lizenznutzung zu verfolgen.

Weitere Informationen zur in diesem Kapitel behandelten Java-API finden Sie unter *Adobe Access API-Referenz*.
