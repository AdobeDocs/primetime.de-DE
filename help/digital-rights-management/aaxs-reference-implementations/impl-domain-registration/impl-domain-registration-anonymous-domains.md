---
seo-title: Anonyme Domänen
title: Anonyme Domänen
uuid: ee29ae4d-65b2-48de-b441-18c8cf55de32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Anonyme Domänen {#anonymous-domains}

In diesem Fall gehören viele Geräte zu einer einzigen Domäne, und eine Authentifizierung ist ggf. nicht erforderlich. Um diesen Domänentyp mit der Referenz-Implementierung zu verwenden, erstellen Sie die Richtlinie, die angibt, dass die Domänenregistrierung erforderlich ist. Geben Sie die URL des Domänenservers an [*!DNL https:// host:port/flashaccess/domainserver/domainname/*] und geben Sie eine anonyme Authentifizierung an.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenregistrierung:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den Domänennamen in der `DomainServerInfo` Tabelle. Wenn ein Eintrag nicht gefunden wird, fügen Sie einen Eintrag in die Tabelle ein (Standardwerte: Authentifizierung ist nicht erforderlich und es ist keine Mitgliedschaft möglich).
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass ein gültiges Authentifizierungstoken in der Anforderung enthalten ist, und stimmen Sie mit dem Auth-Namensraum überein, sofern in der Datenbank angegeben.

   1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken angegeben wurde, geben Sie einen Fehler zurück `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Überprüfen Sie, ob das Gerät bereits bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen in der `DomainMembership` Tabelle. Vergleichen Sie für jede gefundene Computer-GUID mit der GUID des Computers in der Anforderung. Wenn es sich um einen neuen Computer handelt, fügen Sie der `DomainMembership` Tabelle einen Eintrag hinzu.

   1. Wenn es sich um ein neues Gerät handelt und die maximale Mitgliedschaft bereits erreicht wurde, geben Sie einen Fehler zurück `DOM_LIMIT_REACHED (502)`.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der `DomainKeys` Tabelle.

   1. Wenn `DomainServerInfo` dies bedeutet, dass die Schlüssel aktualisiert werden müssen, erstellen Sie ein neues Schlüsselpaar, speichern Sie es in der `DomainKeys` Tabelle (mit einer Schlüsselversion, die höher als der höchste vorhandene Schlüssel ist) und setzen Sie das `Key Rollover Required` Flag in zurück `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenderegistrierung:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den gewünschten Domänennamen in der `DomainServerInfo` Tabelle.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass ein gültiges Authentifizierungstoken in der Anforderung enthalten ist, und stimmen Sie mit dem Auth-Namensraum überein, sofern in der Datenbank angegeben.
1. Suchen Sie den Domänennamen und die Computer-GUID in der `DomainMembership` Tabelle. Wenn ein übereinstimmender Eintrag nicht gefunden wird, wird der Fehler zurückgegeben `DEREG_DENIED (401)`.

1. Wenn dies keine Anforderung zur Vorschau ist, löschen Sie den Eintrag aus `DomainMembership` und setzen Sie das `Key Rollover Required` Flag in `DomainServerInfo`.

In diesem Anwendungsfall ist eine vollständige Übereinstimmung mit der Computer-ID nicht möglich, da eine große Anzahl von Computern der Domäne beitreten könnte. Stattdessen wird die dem Computer während der Individualisierung zugewiesene zufällige Computer-GUID verwendet.
