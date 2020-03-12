---
description: Der SEES-Referenzserver zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.
seo-description: Der SEES-Referenzserver zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.
seo-title: Berechtigung zum Binden von Referenzdienstgeräten
title: Berechtigung zum Binden von Referenzdienstgeräten
uuid: 22ce2f8e-1758-4528-8caf-60d209839afe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Referenz-Dienst: Berechtigung für Gerätebindung {#reference-service-device-binding-entitlement}

Der SEES-Referenzserver zeigt Ihnen, wie Sie den Berechtigungsdienst für die Gerätebindung mit ExpressPlay aktivieren.

>[!NOTE]
>
>Der gerätegebundene Berechtigungsdienst kann auch zeitgebunden sein oder eine Mietdauer vorsehen.

Um die `device_id` Informationen zu bootstrapping zu verwenden, geben Sie einen Platzhalter M3U8-Inhalt wieder. Anschließend können Sie ein Cookie in das ExpressPlay-Token einbetten, eine SPC (die den enthält `device_id`) erstellen und eine `getToken` an den ExpressPlay-Server senden.

![](assets/fees-device-binding.png)

Die Sequenz Beginn durch die Wiedergabe eines Dummy M3U8. Ein Cookie wird an den SEES-Server gesendet, um die URL des ExpressPlay-Tokens abzurufen. Nach dem Empfang der Cookie-gebundenen ExpressPlay-Token-URL wird als Nächstes der SPC generiert und an den ExpressPlay-Server gesendet. Der ExpressPlay-Server extrahiert die `device_id` Daten aus dem SPC, das Cookie aus der ExpressPlay-Token-URL und setzt das Cookie und `device_id` das Transaktionsprotokoll.

Der Kunde stellt eine echte Lizenzanforderung an SEES, das dasselbe Cookie sendet. SEES verwendet das Cookie, um die Daten vom `device_id` ExpressPlay-Server abzurufen.

SEES fordert ein ExpressPlay-Token an, das sowohl gerätegebunden als auch zeitgebunden ist und dieses Token an den Client zurückgibt.

Der Client stellt die Lizenzanforderung mit dem ExpressPlay-Token an.

Der ExpressPlay-Server vergleicht die Datei `device_id` im SPC mit der `device_id` im ExpressPlay-Token. Der ExpressPlay-Server gibt nur dann eine Lizenz aus, wenn die beiden `device_id` Werte übereinstimmen.
