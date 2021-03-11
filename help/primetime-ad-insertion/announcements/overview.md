---
title: Adobe Primetime Ad Insertion-Mitteilungen
description: Ankündigungen zu den neuesten Funktionshinweisen und anderen dazugehörigen Nachrichten über Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Primetime-Ad Insertion-Mitteilungen

## Reduzierung programmatischer Anzeigenfehler über Zeitlimits für die Anzeigenauflösung

Veröffentlicht am 1. Dezember 2000

Die Adobe ist darauf ausgerichtet, unseren Primetime-Ad Insertion-Kunden dabei zu helfen, die Monetarisierung ihres Anzeigenbestands zu maximieren. Besonderes Augenmerk legen wir auf die Reduzierung der Komplexität der Befriedigung der programmatischen Nachfrage, die laut eMarketer über drei Viertel der Ausgaben für digitale Videoanzeigen in den USA ausmacht. Programmgesteuerter Verkauf ermöglicht es Herausgebern, die Nachfrage nach ihrem Anzeigenbestand zu maximieren, was zu höheren Füllraten und Erträgen führt. Es erhöht jedoch auch die Exposition gegenüber Anzeigenfehlern wie fehlerhaften VAST-Antworten, HTTP-Fehlern und anderen, die zu Umsatzeinbußen und/oder schlechten Viewer-Erlebnissen führen können.

Ein häufig auftretendes Problem sind langsame Anzeigenantworten von programmatischen Partnern. In der Regel werden programmatische Anzeigentransaktionen in Millisekunden ausgeführt. Manchmal kann es jedoch zu einer übermäßigen Zeit dauern, bis eine einzige Nachfragequelle reagiert. Eine Verzögerung eines einzelnen Anbieters kann sich auf den gesamten Prozess der Anzeigenbearbeitung auswirken und zu temporären leeren Bildschirmen für den Viewer, nicht ausgefüllten Anzeigenplätzen oder, in Extremfällen, der Notwendigkeit, einen Videostream neu zu starten, führen. Leider stellt die Ermittlung und Umgehung langsamer Nachfragequellen eine große Herausforderung dar.

Um dieses Problem zu beheben, hat Adobe Primetime Ad Insertion neue Tools hinzugefügt, mit denen Kunden zeitliche Beschränkungen für die Anzeigenauflösung festlegen können. Durch das Festlegen dieser Regeln werden langsame Nachfragequellen automatisch umgangen, um sicherzustellen, dass die Videoplayer zeitnah auf Anzeigenantworten zugreifen können. Auf diese Weise können Herausgeber Unterbrechungen durch langsame Nachfragequellen stark begrenzen, wodurch sie die Rate der Lagerbestandsfüllungen maximieren und unterbrechungsfreie, TV-hochwertige Ansichtserlebnisse bereitstellen können.

Um die Zeitüberschreitung bei der Anzeigenauflösung in Primetime Ad Insertion zu aktivieren, ändern Sie Ihre Bootstrap-APIs, um den Parameter ptadtimeout einzuschließen (Dauer in Millisekunden).  Alle Anzeigenanforderungen, die vor der Timeout-Dauer nicht abgeschlossen werden, werden nicht zugeordnet (alle Ausweichanzeigen werden verarbeitet).