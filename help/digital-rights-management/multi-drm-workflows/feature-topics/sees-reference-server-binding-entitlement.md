---
description: Der SEES-Referenzserver zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.
title: Berechtigung zum Binden von Referenzdienstgeräten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Referenz-Dienst: Gerätebindende Berechtigung {#reference-service-device-binding-entitlement}

Der SEES-Referenzserver zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.

>[!NOTE]
>
>Der gerätegebundene Berechtigungsdienst kann auch zeitgebunden sein oder eine Mietdauer vorsehen.

Um die `device_id`-Informationen zu bootstrapping zu verwenden, geben Sie einen Platzhalter M3U8-Inhalt wieder. Sie können dann ein Cookie in das ExpressPlay-Token einbetten, eine SPC generieren (die das `device_id` enthält) und ein `getToken` an den ExpressPlay-Server senden.

![](assets/fees-device-binding.png)

Die Sequenz Beginn durch die Wiedergabe eines Dummy M3U8. Ein Cookie wird an den SEES-Server gesendet, um die URL des ExpressPlay-Tokens abzurufen. Nach dem Empfang der Cookie-gebundenen ExpressPlay-Token-URL wird als Nächstes der SPC generiert und an den ExpressPlay-Server gesendet. Der ExpressPlay-Server extrahiert das `device_id` aus dem SPC, das Cookie aus der ExpressPlay-Token-URL und setzt das Cookie und das `device_id` in das Transaktionsprotokoll.

Der Kunde stellt eine echte Lizenzanforderung an SEES, das dasselbe Cookie sendet. SEES verwendet das Cookie, um das `device_id` vom ExpressPlay-Server abzurufen.

SEES fordert ein ExpressPlay-Token an, das sowohl gerätegebunden als auch zeitgebunden ist und dieses Token an den Client zurückgibt.

Der Client stellt die Lizenzanforderung mit dem ExpressPlay-Token an.

Der ExpressPlay-Server vergleicht das `device_id` in der SPC mit dem `device_id` im ExpressPlay-Token. Der ExpressPlay-Server gibt nur dann eine Lizenz aus, wenn die beiden `device_id`-Werte übereinstimmen.
