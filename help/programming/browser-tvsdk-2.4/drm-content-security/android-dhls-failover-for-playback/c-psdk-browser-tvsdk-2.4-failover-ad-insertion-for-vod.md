---
description: Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss das Browser TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift sie geeignete Maßnahmen.
title: Advertising Insertion and Failover für VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Advertising Insertion and Failover für VOD{#advertising-insertion-and-failover-for-vod}

Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss das Browser TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift sie geeignete Maßnahmen.

## Phase der Anzeigenauflösung {#section_F562CD6D0EF04AA9A0A3C0176A4EC340}

Browser TVSDK kontaktiert einen Dienst zur Anzeigenbereitstellung, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelisten-Datei zu erhalten, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt Browser TVSDK einen HTTP-Aufruf an den Remote-Addelivery-Server durch und analysiert die Antwort des Servers.

Browser TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

  Die Anzeigendaten werden in Text-JSON-Dateien kodiert.
* Adobe Primetime-Anzeigenentscheidungen und -anbieter

  Browser TVSDK sendet eine Anfrage, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Adobe Primetime-Backend-Server für Anzeigenentscheidungen. Adobe Primetime-Anzeigenentscheidungen werden mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache) beantwortet, das die erforderlichen Anzeigeninformationen enthält.

  Eine der folgenden Failover-Situationen kann während dieser Phase auftreten:

   * Die Daten können aus Gründen wie mangelnder Konnektivität oder einem Server-seitigen Fehler nicht abgerufen werden, z. B. weil eine Ressource nicht gefunden werden kann usw.
   * Die Daten wurden abgerufen, das Format ist jedoch ungültig.

     Dies kann beispielsweise dadurch geschehen, dass die Analyse der eingehenden Daten fehlgeschlagen ist.

  Browser TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Anzeigeneinfügephase {#section_88A0E4FA12394717A9D85689BD11D59F}

Browser TVSDK fügt den alternativen Inhalt (Anzeigen) in die Timeline ein, der dem Hauptinhalt entspricht.

Wenn die Phase der Anzeigenauflösung abgeschlossen ist, enthält das Browser TVSDK eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert sind. Jede Werbeunterbrechung wird in der Timeline des Hauptinhalts mit einem Startzeitwert positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung verfügt über eine Eigenschaft &quot;duration&quot;, die ebenfalls in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Daher entspricht die Dauer einer Werbeunterbrechung der Summe der Dauer der einzelnen zusammenstellenden Anzeigen.

Failover kann in dieser Phase mit Konflikten auftreten, die während des Anzeigeneinfügens auf der Timeline auftreten können. Bei bestimmten Kombinationen von Start-/Dauer-Werten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn sich der letzte Teil einer Werbeunterbrechung mit dem Anfang der ersten Anzeige in der nächsten Werbeunterbrechung überschneidet. In diesen Situationen verwirft Browser TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element in der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

Browser TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_7B0073BE9A744C74929263182C1243FC}

Browser TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

An dieser Stelle hat Browser TVSDK aufgelöste Anzeigen, positionierte sie auf der Timeline und versucht, den Inhalt auf dem Bildschirm zu rendern.

Die folgenden Hauptklassen von Fehlern können in dieser Phase auftreten:

* Fehler beim Herstellen einer Verbindung zum Hostserver
* Fehler beim Herunterladen der Manifestdatei
* Fehler beim Herunterladen der Mediensegmente

Für alle drei Fehlerklassen leitet Browser TVSDK ausgelöste Ereignisse an Ihre Anwendung weiter, darunter:

* Benachrichtigungsereignisse werden ausgelöst, wenn ein Failover erfolgt.
* Benachrichtigungsereignisse, wenn das Profil aufgrund des Failover-Algorithmus geändert wird.
* Benachrichtigungsereignisse werden ausgelöst, wenn alle Failover-Optionen berücksichtigt wurden und keine zusätzlichen Aktionen automatisch durchgeführt werden können.

  Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

Ob Fehler auftreten oder nicht, Browser TVSDK benachrichtigt Sie, wenn eine Werbeunterbrechung beginnt und abgeschlossen ist. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Timeline geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielleistenposition und der gemeldete Anzeigenfortschritt zu Unterbrechungen führen.
