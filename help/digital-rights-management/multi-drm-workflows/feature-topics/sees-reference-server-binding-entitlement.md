---
description: Der SEES-Referenz-Server zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.
title: Berechtigung zum Binden von Referenzwängen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Referenz-Dienst: Berechtigung zum Binden von Geräten {#reference-service-device-binding-entitlement}

Der SEES-Referenz-Server zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.

>[!NOTE]
>
>Der gerätegebundene Berechtigungsdienst kann auch zeitgebunden sein oder eine Mietdauer bieten.

Bootstrapping für `device_id` Informationen, Wiedergabe eines Platzhalters M3U8-Inhalts. Sie können dann ein Cookie in das ExpressPlay-Token einbetten und eine SPC generieren (die die Variable `device_id`) und senden Sie eine `getToken` auf den ExpressPlay-Server.

![](assets/fees-device-binding.png)

Die Sequenz beginnt mit dem Abspielen eines Platzhalters M3U8. Ein Cookie wird an den SEES-Server gesendet, um die URL des ExpressPlay-Tokens abzurufen. Nach Erhalt der Cookie-gebundenen ExpressPlay-Token-URL besteht der nächste Schritt darin, die SPC zu generieren und an den ExpressPlay-Server zu senden. Der ExpressPlay-Server extrahiert die `device_id` aus SPC das Cookie aus der ExpressPlay-Token-URL und setzt das Cookie und `device_id` in der Transaktionsprotokolliereinrichtung.

Der Client stellt eine echte Lizenzanfrage an SEES, das denselben Cookie sendet. SEES verwendet das Cookie zum Abrufen der `device_id` vom ExpressPlay-Server aus.

SEES fordert ein ExpressPlay-Token an, das sowohl gerätegebunden als auch zeitgebunden ist, und gibt dieses Token an den Client zurück.

Der Client stellt die Lizenzanfrage mit dem ExpressPlay-Token.

Der ExpressPlay-Server vergleicht die `device_id` in der Zusammenfassung der Merkmale des Arzneimittels mit `device_id` im ExpressPlay-Token. Der ExpressPlay-Server gibt nur dann eine Lizenz aus, wenn die beiden `device_id` -Werte übereinstimmen.
