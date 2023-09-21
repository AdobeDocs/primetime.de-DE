---
description: Durch die Verwendung benutzerdefinierter Anzeigenmarkierungen können Sie bestimmte Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume markieren.
title: Hinzufügen benutzerdefinierter Anzeigenmarken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Übersicht {#add-custom-ad-markers-overview}

Durch die Verwendung benutzerdefinierter Anzeigenmarkierungen können Sie bestimmte Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume markieren.

Diese Funktion ist am nützlichsten, wenn Inhalte beispielsweise von einem Live-Ereignis aufgezeichnet werden und das Ergebnis der Aufzeichnung ein HLS-Stream ist. Die Aufzeichnung enthält Hauptinhalte und werbebezogenen Inhalt in einem HLS-Video-on-Demand (VOD)-Stream. Der Aufnahmevorgang verfolgt nicht die anzeigenbezogenen Segmente, sodass die Informationen, die mit der Positionierung der Anzeigen im Hauptinhalt zusammenhängen, verloren gehen.

Möglicherweise können Sie die Informationen zur Positionierung der Zeiträume für Anzeigeninhalte aus anderen Out-of-Band-Quellen wie externen CMS-Systemen abrufen. Sie können benutzerdefinierte Markierungen definieren, über die diese Out-of-Band-Informationen an das Timeline Manager-Subsystem weitergeleitet werden können. Die Inhaltsabschnitte, die mit dem angegebenen anzeigenbezogenen Inhalt übereinstimmen, sollen so markiert werden, dass alle anzeigenspezifischen Wiedergabeereignisse auf dieselbe Weise ausgelöst werden, als ob diese benutzerdefinierten Anzeigenzeiträume explizit auf der Timeline des Players platziert würden.

Das Anzeigen-Tracking wird nicht intern von TVSDK verarbeitet, z. B. wenn Anzeigen durch Adobe Primetime-Anzeigenentscheidungen (früher Auditude genannt) aufgelöst werden. TVSDK bietet jedoch die folgenden Abstraktionen, die definieren, wie anzeigenbezogene Inhalte auf der Timeline dargestellt werden:

* Die Werbeunterbrechung

  Eine Werbeunterbrechung ist eine geordnete Liste einzelner aufeinander folgender Anzeigen.
* Eine einzelne Anzeige

Wiedergabeereignisse werden separat für Werbeunterbrechungen und Anzeigen am Start- und Endpunkt jeder Anzeige ausgelöst.

TVSDK sendet Anzeigen-Tracking-Ereignisse an Ihre Anwendung, damit Sie Ihre eigene Tracking-Logik implementieren können. Wenn Sie benutzerdefinierte Anzeigenmarkierungen festlegen, erhalten Sie die `onAdBreakStart`, `onAdStart`, `onAdProgress`, `onAdComplete`, und `onAdBreakComplete` -Ereignisse.
