---
description: TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server durch und analysiert die Antwort des Servers.
seo-description: TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server durch und analysiert die Antwort des Servers.
seo-title: Phase der Anzeigenauflösung
title: Phase der Anzeigenauflösung
uuid: b3e62a57-7e62-4e4e-8fa6-0d416785db67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Phase der Anzeigenauflösung{#ad-resolving-phase}

TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

   Die Anzeigendaten werden in einfachen JSON-Dateien kodiert.
* Primetime-Anzeige-Entscheidungsanbieter

   TVSDK sendet eine Anforderung, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Primetime-Back-End-Server für die Anzeigenentscheidung. Die Primetime-Anzeigenentscheidung reagiert mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache), das die erforderlichen Anzeigeninformationen enthält.
* Anbieter von benutzerdefinierten Anzeigenmarken

   Behandelt die Situation, in der Anzeigen vom Server in den Stream verbrannt werden. TVSDK führt nicht die tatsächliche Anzeigeneinfügung durch, sondern muss die auf dem Server eingefügten Anzeigen nachverfolgen. Dieser Anbieter legt die Anzeigenmarken fest, die TVSDK zur Durchführung der Anzeigenverfolgung verwendet.

Während dieser Phase kann eine der folgenden Ausfallsicherungs-Situationen auftreten:

* Die Daten können aus Gründen wie fehlender Konnektivität oder einem serverseitigen Fehler, wie z. B. einer Ressource, nicht gefunden werden usw., nicht abgerufen werden.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

   Dies kann beispielsweise der Fall sein, weil die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.
