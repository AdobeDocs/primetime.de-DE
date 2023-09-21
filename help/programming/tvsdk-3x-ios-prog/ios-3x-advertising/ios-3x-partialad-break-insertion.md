---
description: TVSDK bietet ein TV-ähnliches Erlebnis, in Live-Streams mitmachen zu können.
title: Partielles Einfügen einer Werbeunterbrechung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Partielles Einfügen einer Werbeunterbrechung {#partial-ad-break-insertion}

TVSDK bietet ein TV-ähnliches Erlebnis, in Live-Streams mitmachen zu können.

Mit der Funktion zum Einfügen einer partiellen Werbeunterbrechung können Sie ein TV-ähnliches Erlebnis nachahmen, bei dem der Client einen Live-Stream innerhalb einer Mid-Roll-Datei beginnt, innerhalb dieser Mid-Roll-Phase abzuspielen. Es ähnelt dem Wechsel zu einem Fernsehkanal und die Werbung läuft nahtlos.

Wenn ein Benutzer z. B. mitten in einer 90-Sekunden-Werbeunterbrechung (drei 30-Sekunden-Anzeigen), 10 Sekunden nach der zweiten Anzeige (d. h. nach 40 Sekunden Werbeunterbrechung) Mitglied wird, wird die zweite Anzeige für die verbleibende Dauer (20 Sekunden) und danach die dritte Anzeige wiedergegeben.

## Tracking von Anzeigen {#section_03AFAEAA8DA44399952DC51C5E12951E}

Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Im obigen Beispiel wird nur der Tracker für die dritte Anzeige ausgelöst.

## Verhalten bei Pre-Roll {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

Die Funktion funktioniert, wenn eine Pre-Roll-Anzeige mit Live-Inhalten wiedergegeben wird. Der Stream wird vom Live-Punkt nach Ende der Pre-Roll-Anzeige wiedergegeben.

Werbeunterbrechungsereignisse werden auch dann gesendet, wenn diese Werbeunterbrechung keine vollständigen Anzeigen enthält. Eine Anzeige gilt als partielle Anzeige, wenn länger als eine Sekunde übersprungen wird. Wenn ein Betrachter beispielsweise eine Anzeige sieht, die er 800 ms lang übersprungen hat, wird dies als vollständige Anzeige betrachtet.
