---
description: Mithilfe von benutzerdefinierten Anzeigenmarken können Sie bestimmte Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume markieren.
seo-description: Mithilfe von benutzerdefinierten Anzeigenmarken können Sie bestimmte Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume markieren.
seo-title: hinzufügen von benutzerdefinierten Anzeigenmarken
title: hinzufügen von benutzerdefinierten Anzeigenmarken
uuid: 7cf76e76-965c-4ee4-a311-e28b5a3b5046
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Übersicht {#add-custom-ad-markers-overview}

Mithilfe von benutzerdefinierten Anzeigenmarken können Sie bestimmte Abschnitte des Hauptinhalts als anzeigenbezogene Inhaltszeiträume markieren.

Diese Funktion ist besonders hilfreich, wenn Inhalte beispielsweise aus einem Live-Ereignis aufgezeichnet werden und die Aufzeichnung einen HLS-Stream ergibt. Die Aufzeichnung enthält Hauptinhalte und werbebezogene Inhalte in einem HLS-Video-on-Demand-Stream (VOD). Der Aufzeichnungsprozess verfolgt nicht die mit Anzeigen zusammenhängenden Segmente, sodass die Informationen, die mit der Positionierung der Anzeigen im Hauptinhalt zusammenhängen, verloren gehen.

Möglicherweise können Sie die Informationen zum Positionieren der Zeiträume für Werbeanzeigen aus anderen Out-of-Band-Quellen abrufen, wie z. B. externen CMS-Systemen. Sie können benutzerspezifische Markierungen definieren, mit denen diese Out-of-Band-Informationen an das Timeline Manager-Subsystem weitergeleitet werden können. Die Inhaltsabschnitte, die mit dem angegebenen Werbeinhalt übereinstimmen, sollen so markiert werden, dass alle Ad-spezifischen Wiedergabe-Ereignis auf dieselbe Weise ausgelöst werden, als ob diese benutzerspezifischen Anzeigenzeiträume explizit auf der Zeitleiste des Players platziert würden.

Die Anzeigenverfolgung wird nicht intern von TVSDK verarbeitet, z. B. wenn Anzeigen durch Adobe Primetime-Anzeigenentscheidung (früher als Auditude bekannt) aufgelöst werden. TVSDK bietet jedoch die folgenden Abstraktionen, die definieren, wie werbebezogene Inhalte auf der Zeitschiene dargestellt werden:

* Die Werbeunterbrechung

   Eine Werbeunterbrechung ist eine geordnete Liste von einzelnen aufeinander folgenden Anzeigen.
* Eine einzelne Anzeige

Wiedergabe-Ereignis werden für Werbeunterbrechungen und Anzeigen am Start- und Endpunkt jeder Anzeige separat ausgelöst.

TVSDK sendet Ereignis zur Anzeigenverfolgung an Ihre Anwendung, sodass Sie Ihre eigene Verfolgungslogik implementieren können. Wenn Sie benutzerdefinierte Anzeigenmarken festlegen, erhalten Sie die Ereignis `AD_BREAK_STARTED`, `AD_STARTED`, `AD_PROGRESS`, `AD_COMPLETED` und `AD_BREAK_COMPLETED`.