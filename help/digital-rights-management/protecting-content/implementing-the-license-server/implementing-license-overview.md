---
seo-title: Überblick über den Lizenzserver
title: Überblick über den Lizenzserver
uuid: 8c62376b-b159-4297-9322-75d62947e84e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Übersicht {#license-server-overview}

Bevor Sie Lizenzen für Clients ausstellen können, müssen Sie einen Adobe Primetime DRM-Lizenzserver bereitstellen. Der Lizenzserver verwendet das Primetime DRM SDK, um eine Reihe von Aufgaben durchzuführen.

So implementieren Sie einen Lizenzserver:

* Verarbeiten Sie Authentifizierungsanforderungen, wenn die Authentifizierung mit Benutzername/Kennwort unterstützt wird.
* Lizenzanforderungen bearbeiten
* Serverversionsanforderungen verarbeiten - Alle Server müssen Unterstützung für diesen Anforderungstyp implementieren.
* Anforderungen zur Domänenregistrierung verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Domänenderegistrierungsanforderungen verarbeiten - nur erforderlich, wenn ein Domänenserver implementiert wird.
* Prozesssynchronisierung: Wird nur benötigt, wenn in den Lizenzen die Synchronisierungsanforderungen angegeben sind.

Darüber hinaus muss der Server eine Geschäftslogik für die Authentifizierung von Benutzern bereitstellen, feststellen, ob Benutzer zur Ansicht von Inhalten berechtigt sind, und optional die Lizenznutzung verfolgen.

Weitere Informationen zur Java-API finden Sie unter *Adobe Primetime DRM API-Referenz* .
