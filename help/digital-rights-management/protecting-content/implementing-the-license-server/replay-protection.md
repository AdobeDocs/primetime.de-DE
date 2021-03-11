---
title: Wiederholungsschutz
description: Wiederholungsschutz
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Zum Schutz der Wiederholung der Wiedergabe möchten Sie möglicherweise überprüfen, ob der Meldungsbezeichner vor kurzem durch Aufruf von `RequestMessageBase.getMessageId()` angezeigt wurde. In diesem Fall versucht ein Angreifer möglicherweise, die Anfrage erneut abzuspielen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anforderung gegen die zwischengespeicherte Liste prüfen. Rufen Sie `HandlerConfiguration.setTimestampTolerance()` auf, um die Dauer der Speicherung der Meldungskennungen zu begrenzen. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK dann alle Anforderungen, die einen Zeitstempel für mehr als die angegebene Anzahl von Sekunden nach der Serverzeit enthalten.
