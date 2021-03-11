---
description: TVSDK lädt die Anzeigensegmente herunter und rendert sie auf dem Gerätebildschirm.
title: Phase der Anzeigenwiedergabe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Phase der Anzeigenwiedergabe{#ad-playback-phase}

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

Unabhängig davon, ob Fehler auftreten, ruft TVSDK onAdBreakComplete für jedes `onAdBreakStart` und `onAdComplete` für jedes `onAdStart` auf. Wenn Segmente jedoch nicht heruntergeladen werden konnten, kann es Lücken in der Zeitschiene geben. Wenn die Lücken groß genug sind, können die Werte in der Abspielposition und der gemeldete Anzeigenfortschritt möglicherweise Diskontinuitäten aufweisen.
