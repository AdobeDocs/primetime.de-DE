---
seo-title: Wiederholungsschutz
title: Wiederholungsschutz
uuid: c737998a-9c33-48b4-b741-91106697d71f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Zum Schutz der Wiederholung der Wiedergabe möchten Sie möglicherweise überprüfen, ob der Meldungsbezeichner vor kurzem durch Aufruf von `RequestMessageBase.getMessageId()` angezeigt wurde. In diesem Fall versucht ein Angreifer möglicherweise, die Anfrage erneut abzuspielen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anforderung gegen die zwischengespeicherte Liste prüfen. Rufen Sie `HandlerConfiguration.setTimestampTolerance()` auf, um die Dauer der Speicherung der Meldungskennungen zu begrenzen. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK dann alle Anforderungen, die einen Zeitstempel für mehr als die angegebene Anzahl von Sekunden nach der Serverzeit enthalten.
