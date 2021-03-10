---
description: TVSDK bietet eine TV-ähnliche Erfahrung, in Live-Streams mitmachen zu können.
title: Teilweise Einfügen von Werbeunterbrechungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Teilweise Einfügen von Werbeunterbrechungen {#partial-ad-break-insertion}

TVSDK bietet eine TV-ähnliche Erfahrung, in Live-Streams mitmachen zu können.

Die Funktion zum Einfügen von Werbeunterbrechungen ermöglicht es Ihnen, ein TV-ähnliches Erlebnis zu imitieren, bei dem der Client einen Live-Stream innerhalb einer Mid-Roll-Instanz Beginn, innerhalb dieser Mid-Roll-Version abzuspielen. Es ähnelt dem Wechsel zu einem TV-Kanal und die Werbespots laufen nahtlos.

Wenn sich ein Benutzer beispielsweise in der Mitte einer 90-Sekunden-Werbeunterbrechung (3-30-Sekunden-Anzeige), 10 Sekunden nach der zweiten Anzeige (d. h. 40 Sekunden nach der Werbeunterbrechung) anmeldet, wird die zweite Anzeige für die verbleibende Dauer (20 Sekunden) und anschließend die dritte Anzeige wiedergegeben.

## Track-Anzeige {#section_03AFAEAA8DA44399952DC51C5E12951E}

Anzeigentracker für die teilweise wiedergegebene Anzeige (die zweite Anzeige) werden nicht ausgelöst. Im obigen Beispiel wird nur der Tracker für die dritte Anzeige ausgelöst.

## Verhalten bei Pre-Roll {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

Die Funktion funktioniert, wenn eine Pre-Roll-Anzeige mit Live-Inhalten wiedergegeben wird. Der Stream wird vom Live-Point nach Ende der Pre-Roll-Anzeige wiedergegeben.

Werbeunterbrechungen werden gesendet, auch wenn es in dieser Werbeunterbrechung keine vollständigen Ereignis gibt. Eine Anzeige gilt als Teilanzeige, wenn sie länger als eine Sekunde übersprungen wird. Wenn ein Viewer beispielsweise eine Anzeige sieht, die er 800 ms lang übersprungen hat, wird sie als vollständige Anzeige betrachtet.