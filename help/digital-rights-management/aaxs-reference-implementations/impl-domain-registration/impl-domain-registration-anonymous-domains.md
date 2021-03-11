---
title: Anonyme Domänen
description: Anonyme Domänen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Anonyme Domänen {#anonymous-domains}

In diesem Fall gehören viele Geräte zu einer einzigen Domäne, und eine Authentifizierung ist ggf. nicht erforderlich. Um diesen Domänentyp mit der Referenz-Implementierung zu verwenden, erstellen Sie die Richtlinie, die angibt, dass die Domänenregistrierung erforderlich ist. Geben Sie die URL des Domänenservers als `https:// host:port/flashaccess/domainserver/domainname/` an und geben Sie die anonyme Authentifizierung an.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenregistrierung:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den Domänennamen in der Tabelle `DomainServerInfo`. Wenn ein Eintrag nicht gefunden wird, fügen Sie einen Eintrag in die Tabelle ein (Standardwerte: Authentifizierung ist nicht erforderlich und es ist keine Mitgliedschaft möglich).
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass ein gültiges Authentifizierungstoken in der Anforderung enthalten ist, und stimmen Sie mit dem Auth-Namensraum überein, sofern in der Datenbank angegeben.

   1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken angegeben wurde, geben Sie den Fehler `DOM_AUTHENTICATION_REQUIRED (503)` zurück.

1. Überprüfen Sie, ob das Gerät bereits bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen in der Tabelle `DomainMembership`. Vergleichen Sie für jede gefundene Computer-GUID mit der GUID des Computers in der Anforderung. Wenn dies ein neuer Computer ist, fügen Sie der Tabelle `DomainMembership` einen Eintrag hinzu.

   1. Wenn es sich um ein neues Gerät handelt und die maximale Mitgliedschaft bereits erreicht wurde, geben Sie den Fehler `DOM_LIMIT_REACHED (502)` zurück.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der Tabelle `DomainKeys`.

   1. Wenn `DomainServerInfo` bedeutet, dass die Schlüssel aktualisiert werden müssen, erstellen Sie ein neues Schlüsselpaar, speichern Sie es in der Tabelle `DomainKeys` (mit der Schlüsselversion 1 höher als der höchste vorhandene Schlüssel) und setzen Sie das `Key Rollover Required`-Flag in `DomainServerInfo` zurück.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenderegistrierung:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den angeforderten Domänennamen in der Tabelle `DomainServerInfo`.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass ein gültiges Authentifizierungstoken in der Anforderung enthalten ist, und stimmen Sie mit dem Auth-Namensraum überein, sofern in der Datenbank angegeben.
1. Suchen Sie den Domänennamen und die Computer-GUID in der Tabelle `DomainMembership`. Wenn kein übereinstimmender Eintrag gefunden wird, geben Sie den Fehler `DEREG_DENIED (401)` zurück.

1. Wenn dies keine Anforderung zur Vorschau ist, löschen Sie den Eintrag aus `DomainMembership` und setzen Sie das `Key Rollover Required`-Flag in `DomainServerInfo`.

In diesem Anwendungsfall ist eine vollständige Übereinstimmung mit der Computer-ID nicht möglich, da eine große Anzahl von Computern der Domäne beitreten könnte. Stattdessen wird die dem Computer während der Individualisierung zugewiesene zufällige Computer-GUID verwendet.
