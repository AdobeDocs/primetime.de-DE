---
title: Anonyme Domänen
description: Anonyme Domänen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Anonyme Domänen {#anonymous-domains}

In diesem Anwendungsfall gehört eine große Anzahl von Geräten zu einer Domäne, und eine Authentifizierung ist möglicherweise nicht erforderlich. Um diesen Domänentyp mit der Referenzimplementierung zu verwenden, erstellen Sie die Richtlinie, die angibt, dass die Domänenregistrierung erforderlich ist. Geben Sie die URL des Domänenservers als `https:// host:port/flashaccess/domainserver/domainname/` und geben Sie die anonyme Authentifizierung an.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenregistrierung:

1. Analysieren Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den Domänennamen im `DomainServerInfo` Tabelle. Wenn kein Eintrag gefunden wird, fügen Sie einen Eintrag in die Tabelle ein (Standardwerte: Authentifizierung ist nicht erforderlich und keine Mitgliedschaft ist erlaubt).
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anfrage ein gültiges Authentifizierungstoken enthalten ist, und stimmen Sie mit dem Auth-Namespace überein, sofern in der Datenbank angegeben.

   1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken angegeben wurde, wird ein Fehler zurückgegeben `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Überprüfen Sie, ob das Gerät bereits bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen im `DomainMembership` Tabelle. Vergleichen Sie für jede gefundene Computer-GUID mit der GUID des Computers in der Anfrage. Wenn es sich um einen neuen Computer handelt, fügen Sie dem `DomainMembership` Tabelle.

   1. Wenn es sich um ein neues Gerät handelt und die Max. Mitgliedschaft bereits erreicht wurde, wird ein Fehler zurückgegeben. `DOM_LIMIT_REACHED (502)`.

1. Suchen Sie alle Domain-Schlüssel für diese Domäne im `DomainKeys` Tabelle.

   1. Wenn `DomainServerInfo` gibt an, dass die Schlüssel umgerüstet werden müssen, generiert ein neues Schlüsselpaar, speichert es im `DomainKeys` -Tabelle (mit Schlüsselversion 1 höher als der höchste vorhandene Schlüssel) und setzen Sie die `Key Rollover Required` Markierung in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenderegistrierung:

1. Analysieren Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den angeforderten Domänennamen im `DomainServerInfo` Tabelle.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anfrage ein gültiges Authentifizierungstoken enthalten ist, und stimmen Sie mit dem Auth-Namespace überein, sofern in der Datenbank angegeben.
1. Suchen Sie den Domänennamen und die maschinelle GUID im `DomainMembership` Tabelle. Wenn kein übereinstimmender Eintrag gefunden wird, wird ein Fehler zurückgegeben. `DEREG_DENIED (401)`.

1. Wenn es sich nicht um eine Vorschauanfrage handelt, löschen Sie den Eintrag aus `DomainMembership` und legen Sie die `Key Rollover Required` Markierung in `DomainServerInfo`.

In diesem Anwendungsfall ist es nicht möglich, die Geräte-ID vollständig abzugleichen, da viele Computer der Domäne beitreten könnten. Stattdessen wird die zufällige maschinelle GUID verwendet, die der Maschine während der Individualisierung zugewiesen wurde.
