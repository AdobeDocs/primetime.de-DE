---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Übersicht{#overview}

Um Lizenzen für Clients auszustellen, müssen Sie einen Lizenzserver für Adobe Access bereitstellen. Der Lizenzserver verwendet das Adobe® Access™ SDK, um die folgenden Aufgaben auszuführen:

* Verarbeiten Sie Authentifizierungsanforderungen, wenn die Authentifizierung mit Benutzername/Kennwort unterstützt wird.
* Lizenzanforderungen bearbeiten
* Serverversionsanforderungen verarbeiten - Alle Server müssen Unterstützung für diesen Anforderungstyp implementieren.
* Anforderungen zur Domänenregistrierung verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Domänenderegistrierungsanforderungen verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Prozesssynchronisierung: Nur erforderlich, wenn Lizenzen die Synchronisierungsanforderungen angeben.

Darüber hinaus muss der Server eine Geschäftslogik für die Authentifizierung von Benutzern bereitstellen, feststellen, ob Benutzer zur Ansicht von Inhalten berechtigt sind, und optional die Lizenznutzung verfolgen.

Weitere Informationen zur Java-API, die in diesem Kapitel behandelt werden, finden Sie unter *API-Referenz für den Zugriff auf Adoben*.
