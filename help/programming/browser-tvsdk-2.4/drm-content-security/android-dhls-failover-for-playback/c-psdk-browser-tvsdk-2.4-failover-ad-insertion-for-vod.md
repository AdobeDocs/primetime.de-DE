---
description: Der Video-on-Demand-Anzeigeneinfügeprozess (VOD) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss Browser TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift sie geeignete Maßnahmen.
title: Insertion und Failover von Anzeigen für VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---


# Inserieren und Failover für VOD{#advertising-insertion-and-failover-for-vod}

Der Video-on-Demand-Anzeigeneinfügeprozess (VOD) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss Browser TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift sie geeignete Maßnahmen.

## Phase zur Anzeigenauflösung {#section_F562CD6D0EF04AA9A0A3C0176A4EC340}

Browser TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt Browser TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server aus und analysiert die Antwort des Servers.

Browser TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

   Die Anzeigendaten werden in einfachen JSON-Dateien kodiert.
* Adobe Primetime Ad Decision Ad Provider

   Browser TVSDK sendet eine Anforderung, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Adobe Primetime-Back-End-Server für die Entscheidungsfindung. Adobe Primetime-Anzeigenentscheidungen reagieren mit einem SMIL-Dokument (synchronisierte Multimedia-Integrationssprache), das die erforderlichen Anzeigeninformationen enthält.

   Während dieser Phase kann eine der folgenden Ausfallsicherungs-Situationen auftreten:

   * Die Daten können aus Gründen wie fehlender Konnektivität oder einem serverseitigen Fehler, wie z. B. einer Ressource, nicht gefunden werden usw., nicht abgerufen werden.
   * Die Daten wurden abgerufen, das Format ist jedoch ungültig.

      Dies kann beispielsweise der Fall sein, weil die Analyse der eingehenden Daten fehlgeschlagen ist.
   Browser TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Anzeigeneinfügephase {#section_88A0E4FA12394717A9D85689BD11D59F}

Browser TVSDK fügt den alternativen Inhalt (Anzeigen) in die Zeitleiste ein, die dem Hauptinhalt entspricht.

Wenn die Phase der Anzeigenauflösung abgeschlossen ist, verfügt Browser TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert werden. Jede Werbeunterbrechung wird auf der Timeline des Hauptinhalts mithilfe eines Beginn-Zeitwerts positioniert, der in Millisekunden (ms) ausgedrückt wird. Jede Anzeige in einer Werbeunterbrechung hat eine Eigenschaft &quot;duration&quot;, die auch in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung werden nacheinander miteinander verkettet. Die Dauer einer Werbeunterbrechung entspricht demnach der Summe der Dauer der einzelnen Werbeunterbrechungen.

Failover kann in dieser Phase mit Konflikten auftreten, die auf der Zeitleiste während des Anzeigeneinfügens auftreten können. Bei bestimmten Kombinationen von Beginn-/Zeitwerten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Die Überschneidung tritt auf, wenn der letzte Teil einer Werbeunterbrechung den Anfang der ersten Anzeige in der nächsten Werbeunterbrechung schneidet. In diesen Fällen verwirft Browser TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element auf der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

Browser TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_7B0073BE9A744C74929263182C1243FC}

Browser TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

Zu diesem Zeitpunkt hat Browser TVSDK aufgelöste Anzeigen, positionierte sie auf der Zeitleiste und versucht, den Inhalt auf dem Bildschirm wiederzugeben.

Die folgenden Hauptklassen von Fehlern können in dieser Phase auftreten:

* Fehler beim Herstellen einer Verbindung mit dem Hostserver
* Fehler beim Herunterladen der Manifestdatei
* Fehler beim Herunterladen der Mediensegmente

Für alle drei Fehlerklassen löste Browser TVSDK weitergeleitete Ereignis in Ihrer Anwendung aus, darunter:

* Benachrichtigungs-Ereignis werden ausgelöst, wenn ein Failover eintritt.
* Benachrichtigungs-Ereignis, wenn das Profil aufgrund des Failover-Algorithmus geändert wird.
* Benachrichtigungsfehler werden ausgelöst, wenn alle Failover-Optionen in Betracht gezogen wurden und keine zusätzlichen Ereignis automatisch ausgeführt werden können.

   Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

Ob Fehler auftreten oder nicht, Browser TVSDK benachrichtigt Sie, wenn eine Werbeunterbrechung Beginn wird und wenn sie abgeschlossen ist. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Zeitschiene geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielposition und der gemeldete Anzeigenfortschritt möglicherweise Diskontinuitäten aufweisen.
