---
seo-title: Wiederholungsschutz
title: Wiederholungsschutz
uuid: 75f2be65-b2fc-428a-b853-34a4b30960ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Wiederholungsschutz{#replay-protection}

Zum Schutz vor Wiederholungen ist es ggf. sinnvoll zu prüfen, ob der Meldungsbezeichner kürzlich durch Aufruf von `RequestMessageBase.getMessageId()` erkannt wurde. In diesem Fall versucht ein Angreifer möglicherweise, die Anfrage erneut abzuspielen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anforderung gegen die zwischengespeicherte Liste prüfen. Rufen Sie `HandlerConfiguration.setTimestampTolerance()` auf, um die Dauer der Speicherung der Meldungskennungen zu begrenzen. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK alle Anforderungen, die einen Zeitstempel enthalten, der länger als die angegebene Anzahl von Sekunden vor der Serverzeit ist.
