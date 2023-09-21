---
description: TVSDK kontaktiert einen Dienst zur Anzeigenbereitstellung, z. B. Adobe Primetime und versucht, die primäre Wiedergabelistendatei zu erhalten, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Addelivery-Server durch und analysiert die Antwort des Servers.
title: Phase der Anzeigenauflösung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Phase der Anzeigenauflösung{#ad-resolving-phase}

TVSDK kontaktiert einen Dienst zur Anzeigenbereitstellung, z. B. Adobe Primetime und versucht, die primäre Wiedergabelistendatei zu erhalten, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Addelivery-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

  Die Anzeigendaten werden in Text-JSON-Dateien kodiert.
* Primetime-Anzeigenentscheidungen und -anbieter

  TVSDK sendet eine Anfrage, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Back-End-Server für Primetime-Anzeigenentscheidungen. Die Primetime-Anzeigenentscheidung antwortet mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache), das die erforderlichen Anzeigeninformationen enthält.
* Benutzerspezifischer Anbieter von Anzeigenmarken

  Beseitigt die Situation, in der Anzeigen vom Server in den Stream verbrannt werden. TVSDK führt keine tatsächliche Anzeigeneinfügung durch, muss jedoch die Anzeigen verfolgen, die auf der Server-Seite eingefügt wurden. Dieser Provider legt die Anzeigenmarken fest, die TVSDK zur Durchführung des Anzeigen-Trackings verwendet.

Eine der folgenden Failover-Situationen kann während dieser Phase auftreten:

* Die Daten können aus Gründen wie mangelnder Konnektivität oder einem Server-seitigen Fehler nicht abgerufen werden, z. B. weil eine Ressource nicht gefunden werden kann usw.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

  Dies kann beispielsweise dadurch geschehen, dass die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.
