---
description: Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift sie geeignete Maßnahmen.
title: Advertising Insertion and Failover für VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Advertising Insertion and Failover für VOD{#advertising-insertion-and-failover-for-vod}

Der Video-On-Demand (VOD)-Anzeigeneinfüge-Prozess besteht aus den Phasen der Anzeigenauflösung, des Anzeigeneinfügens und der Anzeigenwiedergabe. Für das Anzeigen-Tracking muss TVSDK einen Remote-Tracking-Server über den Wiedergabestatus jeder Anzeige informieren. Wenn unerwartete Situationen auftreten, ergreift sie geeignete Maßnahmen.

## Phase der Anzeigenauflösung {#section_0D45C6094D724B55868B48F9A3557A8B}

TVSDK kontaktiert einen Dienst zur Anzeigenbereitstellung, z. B. Adobe Primetime und versucht, die primäre Wiedergabelistendatei zu erhalten, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Addelivery-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

  Die Anzeigendaten werden in Text-JSON-Dateien kodiert.
* Primetime-Anzeigenentscheidungen und -anbieter

  TVSDK sendet eine Anfrage, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Back-End-Server für Primetime-Anzeigenentscheidungen. Die Primetime-Anzeigenentscheidung antwortet mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache), das die erforderlichen Anzeigeninformationen enthält.

Eine der folgenden Failover-Situationen kann während dieser Phase auftreten:

* Die Daten können aus Gründen wie mangelnder Konnektivität oder einem Server-seitigen Fehler nicht abgerufen werden, z. B. weil eine Ressource nicht gefunden werden kann usw.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

  Dies kann beispielsweise dadurch geschehen, dass die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Anzeigeneinfügephase {#section_1B18E8B5768B4873B3346294175B7340}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Timeline ein, der dem Hauptinhalt entspricht.

Wenn die Phase der Anzeigenauflösung abgeschlossen ist, verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert sind. Jede Werbeunterbrechung wird in der Timeline des Hauptinhalts mit einem Startzeitwert positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung verfügt über eine Eigenschaft &quot;duration&quot;, die ebenfalls in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Daher entspricht die Dauer einer Werbeunterbrechung der Summe der Dauer der einzelnen zusammenstellenden Anzeigen.

Failover kann in dieser Phase mit Konflikten auftreten, die während des Anzeigeneinfügens auf der Timeline auftreten können. Bei bestimmten Kombinationen von Start-/Dauer-Werten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn sich der letzte Teil einer Werbeunterbrechung mit dem Anfang der ersten Anzeige in der nächsten Werbeunterbrechung überschneidet. In diesen Situationen verwirft die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element in der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und setzt die Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_64777BD2CDA84EACB0A4EA6D68367CF5}

TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

Zu diesem Zeitpunkt hat TVSDK aufgelöste Anzeigen platziert, sie auf der Timeline positioniert und versucht, den Inhalt auf dem Bildschirm zu rendern.

Die folgenden Hauptklassen von Fehlern können in dieser Phase auftreten:

* Fehler beim Herstellen einer Verbindung zum Hostserver
* Fehler beim Herunterladen der Manifestdatei
* Fehler beim Herunterladen der Mediensegmente

Für alle drei Fehlerklassen leitet TVSDK ausgelöste Ereignisse an Ihre Anwendung weiter, darunter:

* Benachrichtigungsereignisse werden ausgelöst, wenn ein Failover erfolgt.
* Benachrichtigungsereignisse, wenn das Profil aufgrund des Failover-Algorithmus geändert wird.
* Benachrichtigungsereignisse werden ausgelöst, wenn alle Failover-Optionen berücksichtigt wurden und keine zusätzlichen Aktionen automatisch durchgeführt werden können.

  Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

Ob Fehler auftreten oder nicht, TVSDK-Aufrufe `AdBreakPlaybackEvent.AD_BREAK_COMPLETE` für jeden `AdBreakPlaybackEvent.AD_BREAK_STARTED` und `AdPlaybackEvent.AD_COMPLETED` für jeden `AdPLaybackEvent.AD_STARTED`. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Timeline geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielleistenposition und der gemeldete Anzeigenfortschritt zu Unterbrechungen führen.
