---
title: Wiederholungsschutz
description: Wiederholungsschutz
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Wiederholungsschutz{#replay-protection}

Zum Schutz der Wiederholung kann es ratsam sein, zu überprüfen, ob die Nachrichtenkennung kürzlich durch Aufruf von `RequestMessageBase.getMessageId()`. Wenn ja, könnte ein Angreifer versuchen, die Anfrage erneut auszuführen, was verweigert werden sollte. Um Wiederholungsversuche zu erkennen, kann der Server eine Liste der kürzlich angezeigten Nachrichten-IDs speichern und jede eingehende Anfrage mit der zwischengespeicherten Liste vergleichen. Rufen Sie auf, um die Dauer der Speicherung der Nachrichtenbezeichner zu begrenzen. `HandlerConfiguration.setTimestampTolerance()`. Wenn diese Eigenschaft festgelegt ist, verweigert das SDK alle Anfragen, die einen Zeitstempel enthalten, der länger als die angegebene Anzahl von Sekunden vor der Serverzeit ist.
