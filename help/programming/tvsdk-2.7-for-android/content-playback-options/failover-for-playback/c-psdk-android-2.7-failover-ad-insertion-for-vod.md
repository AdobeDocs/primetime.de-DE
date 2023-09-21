---
description: Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift TVSDK geeignete Maßnahmen.
title: Advertising Insertion and Failover für VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# Advertising Insertion and Failover für VOD {#advertising-insertion-and-failover-for-vod}

Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift TVSDK geeignete Maßnahmen.

## Phase der Anzeigenauflösung {#section_5DD3A7DA79E946298BFF829A60202E1C}

TVSDK kontaktiert einen Dienst zur Anzeigenbereitstellung, z. B. Adobe Primetime und versucht, die primäre Wiedergabelistendatei zu erhalten, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Addelivery-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

  Die Anzeigendaten werden in Text-JSON-Dateien kodiert.
* Primetime-Anzeigenentscheidungen und -anbieter

  TVSDK sendet eine Anfrage, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Primetime-Back-End-Server für Anzeigenentscheidungen. Die Primetime-Anzeigenentscheidung antwortet mit einem synchronisierten SMIL-Dokument (Multimedia Integration Language), das die erforderlichen Anzeigeninformationen enthält.
* Benutzerspezifischer Anbieter von Anzeigenmarken

  Beseitigt die Situation, in der Anzeigen vom Server in den Stream verbrannt werden. TVSDK führt keine tatsächliche Anzeigeneinfügung durch, muss jedoch die Anzeigen verfolgen, die auf der Server-Seite eingefügt wurden. Dieser Provider legt die Anzeigenmarken fest, die TVSDK zur Durchführung des Anzeigen-Trackings verwendet.

Eine der folgenden Failover-Situationen kann während dieser Phase auftreten:

* Die Daten können nicht abgerufen werden, weil beispielsweise keine Verbindung oder ein Server-seitiger Fehler wie eine Ressource nicht gefunden werden kann usw.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

  Dies kann beispielsweise dadurch geschehen, dass die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Anzeigeneinfügephase {#section_29F7F7756C8B40B99AD4C3DD16B72B5B}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Timeline ein, der dem Hauptinhalt entspricht.

Wenn die Phase der Anzeigenauflösung abgeschlossen ist, verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert sind. Jede Werbeunterbrechung wird mithilfe eines in Millisekunden (ms) ausgedrückten Startzeitwerts auf der Timeline des Hauptinhalts positioniert. Jede Anzeige in einer Werbeunterbrechung verfügt über eine Eigenschaft &quot;duration&quot;, die ebenfalls in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung sind verkettet, sodass die Dauer einer Werbeunterbrechung der Summe der Dauer der einzelnen Werbeunterbrechungen entspricht.

Failover kann in dieser Phase mit Konflikten auftreten, die während des Anzeigeneinfügens auf der Timeline auftreten können. Bei bestimmten Kombinationen von Start-/Dauer-Werten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Diese Überschneidung tritt auf, wenn sich der letzte Teil einer Werbeunterbrechung mit dem Anfang der ersten Anzeige in der nächsten Werbeunterbrechung überschneidet. In diesen Situationen verwirft TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element in der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_DA816F88AF8A4A5A8FD0DE2D54A86031}

TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

TVSDK hat jetzt aufgelöste Anzeigen, positionierte Anzeigen auf der Timeline und versucht, den Inhalt auf dem Bildschirm zu rendern.

Die folgenden Hauptklassen von Fehlern können in den folgenden Phasen auftreten:

* Beim Herstellen einer Verbindung zum Hostserver.
* Beim Herunterladen der Manifestdatei.
* Beim Herunterladen der Mediensegmente.

TVSDK leitet die ausgelösten Ereignisse an Ihre Anwendung weiter, einschließlich Benachrichtigungsereignissen, die ausgelöst werden, wenn:

* Ein Failover erfolgt.
* Das Profil wird aufgrund des Failover-Algorithmus geändert.
* Alle Failover-Optionen wurden berücksichtigt und es können keine zusätzlichen Aktionen automatisch durchgeführt werden.

  Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

TVSDK-Aufrufe, unabhängig davon, ob Fehler auftreten `onAdBreakComplete` für jeden `onAdBreakStart` und `onAdComplete` für jeden `onAdStart`. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Timeline geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielleistenposition und der gemeldete Anzeigenfortschritt zu Unterbrechungen führen.
