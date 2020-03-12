---
description: Der Video-on-Demand-Anzeigeneinfügeprozess (VOD) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift TVSDK geeignete Maßnahmen.
seo-description: Der Video-on-Demand-Anzeigeneinfügeprozess (VOD) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift TVSDK geeignete Maßnahmen.
seo-title: Insertion und Failover von Anzeigen für VOD
title: Insertion und Failover von Anzeigen für VOD
uuid: 74cc35e6-6479-4572-a3b3-05ff6344272a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Insertion und Failover von Anzeigen für VOD {#advertising-insertion-and-failover-for-vod}

Der Video-on-Demand-Anzeigeneinfügeprozess (VOD) besteht aus der Phase der Auflösung der Anzeige, des Einfügens der Anzeige und der Wiedergabe der Anzeige. Zur Anzeigenverfolgung muss TVSDK einen Remote-Tracking-Server über den Wiedergabegeschwindigkeit jeder Anzeige informieren. Treten unerwartete Situationen auf, ergreift TVSDK geeignete Maßnahmen.

## Phase der Anzeigenauflösung {#section_5DD3A7DA79E946298BFF829A60202E1C}

TVSDK kontaktiert einen Anzeigen-Versand-Dienst, z. B. Adobe Primetime-Anzeigenentscheidung, und versucht, die primäre Wiedergabelistendatei abzurufen, die dem Videostream für die Anzeige entspricht. Während der Phase der Anzeigenauflösung führt TVSDK einen HTTP-Aufruf an den Remote-Ad-Versand-Server durch und analysiert die Antwort des Servers.

TVSDK unterstützt die folgenden Arten von Anzeigenanbietern:

* Metadaten-Anzeigenanbieter

   Die Anzeigendaten werden in einfachen JSON-Dateien kodiert.
* Primetime-Anzeige-Entscheidungsanbieter

   TVSDK sendet eine Anforderung, einschließlich einer Reihe von Targeting-Parametern und einer Asset-Identifikationsnummer, an den Primetime-Ad-Decision-Back-End-Server. Die Primetime-Anzeigenentscheidung reagiert mit einem synchronisierten SMIL-Dokument (Multimedia Integration Language), das die erforderlichen Anzeigeninformationen enthält.
* Anbieter von benutzerdefinierten Anzeigenmarken

   Behandelt die Situation, in der Anzeigen vom Server in den Stream verbrannt werden. TVSDK führt keine tatsächliche Anzeigeneinfügung durch, muss jedoch die auf dem Server eingefügten Anzeigen verfolgen. Dieser Anbieter legt die Anzeigenmarken fest, die TVSDK zur Durchführung der Anzeigenverfolgung verwendet.

Während dieser Phase kann eine der folgenden Ausfallsicherungs-Situationen auftreten:

* Die Daten können nicht abgerufen werden, weil beispielsweise keine Verbindung besteht oder ein serverseitiger Fehler, wie z. B. eine Ressource, nicht gefunden werden kann usw.
* Die Daten wurden abgerufen, das Format ist jedoch ungültig.

   Dies kann beispielsweise der Fall sein, weil die Analyse der eingehenden Daten fehlgeschlagen ist.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Anzeigeneinfügephase {#section_29F7F7756C8B40B99AD4C3DD16B72B5B}

TVSDK fügt den alternativen Inhalt (Anzeigen) in die Zeitleiste ein, die dem Hauptinhalt entspricht.

Nach Abschluss der Phase der Anzeigenauflösung verfügt TVSDK über eine geordnete Liste von Anzeigenressourcen, die in Werbeunterbrechungen gruppiert werden. Jede Werbeunterbrechung wird auf der Timeline des Hauptinhalts mithilfe eines Beginn-Zeitwerts in Millisekunden (ms) positioniert. Jede Anzeige in einer Werbeunterbrechung hat eine Eigenschaft &quot;duration&quot;, die auch in ms ausgedrückt wird. Die Anzeigen in einer Werbeunterbrechung sind verkettet, und infolgedessen entspricht die Dauer einer Werbeunterbrechung der Summe der Dauer der einzelnen Werbeanzeigen.

Failover kann in dieser Phase mit Konflikten auftreten, die auf der Zeitleiste während des Anzeigeneinfügens auftreten können. Bei bestimmten Kombinationen von Beginn-/Zeitwerten für Werbeunterbrechungen können sich Anzeigensegmente überschneiden. Diese Überschneidung tritt auf, wenn der letzte Teil einer Werbeunterbrechung den Anfang der ersten Anzeige in der nächsten Werbeunterbrechung schneidet. In diesen Fällen verwirft TVSDK die spätere Werbeunterbrechung und setzt den Anzeigeneinfügeprozess mit dem nächsten Element auf der Liste fort, bis alle Werbeunterbrechungen eingefügt oder verworfen werden.

TVSDK gibt eine Warnmeldung zum Fehler aus und fährt mit der Verarbeitung fort.

## Phase der Anzeigenwiedergabe {#section_DA816F88AF8A4A5A8FD0DE2D54A86031}

TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.

TVSDK hat jetzt Anzeigen aufgelöst, die Anzeigen auf der Zeitleiste positioniert und versucht, den Inhalt auf dem Bildschirm wiederzugeben.

Die folgenden Hauptklassen von Fehlern können in den folgenden Phasen auftreten:

* Beim Herstellen einer Verbindung mit dem Hostserver.
* Beim Herunterladen der Manifestdatei.
* Beim Herunterladen der Mediensegmente.

TVSDK leitet die ausgelösten Ereignis an Ihre Anwendung weiter, einschließlich Benachrichtigungs-Ereignissen, die ausgelöst werden, wenn:

* Ein Failover erfolgt.
* Das Profil wird aufgrund des Failover-Algorithmus geändert.
* Alle Ausfallsicherungsoptionen wurden in Betracht gezogen, und es können keine zusätzlichen Aktionen automatisch durchgeführt werden.

   Ihre Anwendung muss die entsprechenden Maßnahmen ergreifen.

Ganz gleich, ob Fehler auftreten, TVSDK ruft `onAdBreakComplete` für jeden `onAdBreakStart` und `onAdComplete` für jeden auf `onAdStart`. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Zeitschiene geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielposition und der gemeldete Anzeigenfortschritt möglicherweise Diskontinuitäten aufweisen.