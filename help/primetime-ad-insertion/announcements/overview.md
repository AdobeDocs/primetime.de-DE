---
title: Adobe Primetime Ad Insertion-Ankündigungen
description: Ankündigungen zu aktuellen Funktionsveröffentlichungen und anderen zugehörigen Neuigkeiten über Primetime-Ad Insertion
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Primetime-Ad Insertion-Ankündigungen

## Verringerung programmatischer Anzeigenfehler über Zeitüberschreitungen bei der Anzeigenauflösung

Veröffentlicht am 1. Dezember 2020

Adobe konzentriert sich darauf, unseren Primetime-Ad Insertion-Kunden zu helfen, die Monetarisierung ihres Anzeigenbestands zu maximieren. Besonderes Augenmerk legen wir auf die Reduzierung der Komplexität bei der Erfüllung der programmatischen Nachfrage, die laut eMarketer über drei Viertel der Ausgaben für digitale Videoanzeigen in den USA ausmacht. Programmgesteuerter Verkauf ermöglicht es Herausgebern, die Nachfrage nach ihrem Anzeigenbestand zu maximieren, was zu höheren Füllraten und Erträgen führt. Es erhöht jedoch auch die Exposition gegenüber Anzeigenfehlern wie falsch formatierten VAST-Antworten, HTTP-Fehlern und anderen, die zu Umsatzverlusten und/oder schlechten Viewer-Erlebnissen führen können.

Ein häufiges Problem sind langsame Anzeigenantworten von programmatischen Partnern. In der Regel treten programmatische Anzeigentransaktionen in Millisekunden auf. Manchmal kann es jedoch übermäßig lange dauern, bis eine einzige Nachfragequelle reagiert. Eine Verzögerung durch einen einzelnen Anbieter kann sich auf den gesamten Prozess der Anzeigenbearbeitung auswirken und temporäre leere Bildschirme für den Viewer, nicht ausgefüllte Anzeigenplätze oder in Extremfällen die Notwendigkeit verursachen, einen Video-Stream neu zu starten. Leider ist die Ermittlung und Umgehung langsamer Nachfragequellen eine große Herausforderung.

Um dieses Problem zu beheben, hat Adobe neue Tools zu Primetime Ad Insertion hinzugefügt, mit denen Kunden Zeitbeschränkungen für die Anzeigenauflösung festlegen können. Durch das Festlegen dieser Regeln werden langsame Nachfragequellen automatisch umgangen, sodass die Videoplayer zeitnah Anzeigenantworten erhalten. Auf diese Weise können Herausgeber Unterbrechungen durch langsame Nachfragequellen stark einschränken, wodurch sie die Inventarfüllraten maximieren und unterbrechungsfreie Fernseherlebnisse bereitstellen können.

Um das Zeitlimit für die Anzeigenauflösung in Primetime Ad Insertion zu aktivieren, ändern Sie Ihre Bootstrap-APIs so, dass der Parameter ptadtimeout (Dauer in Millisekunden) enthalten ist.  Ad-Anfragen, die vor Ablauf der Zeitüberschreitung nicht abgeschlossen werden, werden nicht zugeordnet (alle Fallback-Anzeigen werden verarbeitet).
