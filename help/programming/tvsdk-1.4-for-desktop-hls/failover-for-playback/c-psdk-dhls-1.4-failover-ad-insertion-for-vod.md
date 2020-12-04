---
description: Der VOD-Anzeigeneinfügeprozess (video-on-demand) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift sie geeignete Maßnahmen.
seo-description: Der VOD-Anzeigeneinfügeprozess (video-on-demand) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift sie geeignete Maßnahmen.
seo-title: Insertion und Failover von Anzeigen für VOD
title: Insertion und Failover von Anzeigen für VOD
uuid: 98505f63-ac43-4ff5-9f7b-895b6135df47
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---


# Inserieren und Failover für VOD{#advertising-insertion-and-failover-for-vod}

Der VOD-Anzeigeneinfügeprozess (video-on-demand) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift sie geeignete Maßnahmen.

## Phase zur Anzeigenauflösung {#section_0D45C6094D724B55868B48F9A3557A8B}

TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

   Die Anzeigendaten werden in einfachen JSON-Dateien kodiert.
* Primetime-Anzeige-Entscheidungsanbieter

   TVSDK sendet eine Anforderung, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Primetime-Back-End-Server für die Anzeigenentscheidung. Die Primetime-Anzeigenentscheidung reagiert mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache), das die erforderlichen Anzeigeninformationen enthält.

Während dieser Phase kann eine der folgenden Ausfallsicherungs-Situationen auftreten:

* Die Daten können aus Gründen wie fehlender Konnektivität oder einem serverseitigen Fehler, wie z. B. einer Ressource, nicht gefunden werden usw., nicht abgerufen werden.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

   Dies kann beispielsweise der Fall sein, weil die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Anzeigeneinfügephase {#section_1B18E8B5768B4873B3346294175B7340}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Zeitleiste ein, die dem Hauptinhalt entspricht.

Nach Abschluss der Phase der Anzeigenauflösung verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert werden. Jede Werbeunterbrechung wird auf der Timeline des Hauptinhalts mithilfe eines Beginn-Zeitwerts positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung hat eine Eigenschaft &quot;duration&quot;, die auch in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Die Dauer einer Werbeunterbrechung entspricht demnach der Summe der Dauer der einzelnen Werbeunterbrechungen.

Failover kann in dieser Phase mit Konflikten auftreten, die auf der Zeitleiste während des Anzeigeneinfügens auftreten können. Bei bestimmten Kombinationen von Beginn-/Zeitwerten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn der letzte Teil einer Werbeunterbrechung den Anfang der ersten Anzeige in der nächsten Werbeunterbrechung schneidet. In diesen Fällen wird der spätere Werbeunterbrechung verworfen und der Anzeigeneinfügeprozess mit dem nächsten Element auf der Liste fortgesetzt, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_64777BD2CDA84EACB0A4EA6D68367CF5}

TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

Zu diesem Zeitpunkt hat TVSDK Anzeigen aufgelöst, positioniert sie auf der Zeitleiste und versucht, den Inhalt auf dem Bildschirm zu rendern.

Die folgenden Hauptklassen von Fehlern können in dieser Phase auftreten:

* Fehler beim Herstellen einer Verbindung mit dem Hostserver
* Fehler beim Herunterladen der Manifestdatei
* Fehler beim Herunterladen der Mediensegmente

Für alle drei Fehlerklassen löste TVSDK weitergeleitete Ereignis in Ihrer Anwendung aus, darunter:

* Benachrichtigungs-Ereignis werden ausgelöst, wenn ein Failover eintritt.
* Benachrichtigungs-Ereignis, wenn das Profil aufgrund des Failover-Algorithmus geändert wird.
* Benachrichtigungsfehler werden ausgelöst, wenn alle Failover-Optionen in Betracht gezogen wurden und keine zusätzlichen Ereignis automatisch ausgeführt werden können.

   Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

Unabhängig davon, ob Fehler auftreten, ruft TVSDK für jedes `AdBreakPlaybackEvent.AD_BREAK_COMPLETE`- und `AdBreakPlaybackEvent.AD_BREAK_STARTED`-Element `AdPlaybackEvent.AD_COMPLETED`- auf. `AdPLaybackEvent.AD_STARTED` Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Zeitschiene geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielposition und der gemeldete Anzeigenfortschritt möglicherweise Diskontinuitäten aufweisen.
