---
seo-title: Übersicht
title: Übersicht
uuid: f4ae10ca-6e2a-4313-80a0-4c7377dba000
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht{#overview}

Um Lizenzen an Clients auszustellen, müssen Sie einen Adobe Access-Lizenzserver bereitstellen. Der Lizenzserver verwendet das Adobe® Access™ SDK, um die folgenden Aufgaben auszuführen:

* Verarbeiten Sie Authentifizierungsanforderungen, wenn die Authentifizierung mit Benutzername/Kennwort unterstützt wird.
* Lizenzanforderungen bearbeiten
* Serverversionsanforderungen verarbeiten - Alle Server müssen Unterstützung für diesen Anforderungstyp implementieren.
* Anforderungen zur Domänenregistrierung verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Domänenderegistrierungsanforderungen verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Prozesssynchronisierung: Nur erforderlich, wenn Lizenzen die Synchronisierungsanforderungen angeben.

Darüber hinaus muss der Server eine Geschäftslogik für die Authentifizierung von Benutzern bereitstellen, feststellen, ob Benutzer zur Ansicht von Inhalten berechtigt sind, und optional die Lizenznutzung verfolgen.

Weitere Informationen zur Java-API, die in diesem Kapitel besprochen werden, finden Sie in der *Adobe Access-API-Referenz*.
