---
title: Übersicht über den Lizenzserver
description: Übersicht über den Lizenzserver
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Übersicht {#license-server-overview}

Bevor Sie Lizenzen für Clients erteilen können, müssen Sie einen Adobe Primetime DRM-Lizenzserver bereitstellen. Der Lizenzserver verwendet das Primetime DRM SDK, um eine Reihe von Aufgaben auszuführen.

So implementieren Sie einen Lizenzserver:

* Verarbeiten Sie Authentifizierungsanfragen, wenn die Authentifizierung mit Benutzername/Kennwort unterstützt wird.
* Lizenzanforderungen bearbeiten
* Verarbeitung von Server-Versionsanfragen - Alle Server müssen Unterstützung für diesen Anforderungstyp implementieren.
* Registrierungsanfragen für Domänen verarbeiten - nur bei Implementierung eines Domänenservers erforderlich.
* Domänenderegistrierungsanfragen verarbeiten - nur bei Implementierung eines Domänenservers erforderlich.
* Synchronisation von Prozessen - nur erforderlich, wenn in Lizenzen Synchronisierungsanforderungen angegeben sind.

Darüber hinaus muss der Server Geschäftslogik für die Authentifizierung von Benutzern bereitstellen, um zu bestimmen, ob Benutzer berechtigt sind, Inhalte anzuzeigen und optional die Lizenznutzung zu verfolgen.

Siehe *Adobe Primetime DRM API-Referenz* für Details zur Java-API.
