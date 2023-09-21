---
description: TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.
title: Phase der Anzeigenwiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Phase der Anzeigenwiedergabe{#ad-playback-phase}

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

Unabhängig davon, ob Fehler auftreten, ruft TVSDK für jede `onAdBreakStart` und `onAdComplete` für jeden `onAdStart`. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Timeline geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielleistenposition und der gemeldete Anzeigenfortschritt zu Unterbrechungen führen.
