---
description: 'null'
seo-description: 'null'
seo-title: Anonyme Domänenlogik
title: Anonyme Domänenlogik
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Anonyme Domänenlogik{#anonymous-domain-logic}

## Domänenregistrierungslogik {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

Die Referenzimplementierung wendet die folgende Logik für die anonyme Domänenregistrierung an:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den Domänennamen in der `DomainServerInfo` Tabelle.
1. Wenn Sie einen Eintrag nicht finden können, fügen Sie einen Eintrag in die Tabelle ein.

   Die Standardwerte sind:

   * `authentication is not required`
   * `no membership maximum`
   Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anforderung ein gültiges Authentifizierungstoken vorhanden ist. Wenn der Auth-Namensraum in der Datenbank angegeben ist, muss das Token mit dem angegebenen Auth-Namensraum übereinstimmen.
1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken verfügbar ist, geben Sie einen Fehler zurück `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Überprüfen Sie, ob das Gerät bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen in der `DomainMembership` Tabelle.
   1. Vergleichen Sie die GUID des Computers, die Sie in der Anforderung finden, mit der GUID des Computers.
   1. Wenn es sich um einen neuen Computer handelt, fügen Sie einen Eintrag in der `DomainMembership` Tabelle hinzu.
   1. Wenn es sich um ein neues Gerät handelt und der `Max Membership` Wert erreicht wurde, geben Sie einen Fehler zurück `DOM_LIMIT_REACHED (502)`.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der `DomainKeys` Tabelle:

   1. Wenn `DomainServerInfo` dies bedeutet, dass die Tasten aktualisiert werden müssen, erstellen Sie ein neues Schlüsselpaar.
   1. Speichern Sie die Tastenkombination in der `DomainKeys` Tabelle mit einer Schlüsselversion, die eine Zahl höher ist als der höchste vorhandene Schlüssel.
   1. Setzen Sie die `Key Rollover Required` Markierung zurück in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domänenderegistrierungslogik {#section_C968BBFCBFAB4510A903D169F38C9FCE}

Die Referenzimplementierung wendet die folgende Logik für die anonyme Domänenderegistrierung an:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den gewünschten Domänennamen in der `DomainServerInfo` Tabelle.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anforderung ein gültiges Authentifizierungstoken vorhanden ist.

   Das Token muss auch mit dem Auth-Namensraum übereinstimmen, der in der Datenbank angegeben ist.
1. Suchen Sie den Domänennamen und die Computer-GUID in der `DomainMembership` Tabelle.

   Wenn Sie keinen übereinstimmenden Eintrag finden können, geben Sie einen Fehler zurück `DEREG_DENIED (401)`.

1. Wenn es sich nicht um eine Anforderung zur Vorschau handelt, löschen Sie den Eintrag aus `DomainMembership`und setzen Sie `DomainServerInfo`das `Key Rollover Required` Flag.

Da viele Computer der Domäne beitreten können, können Sie nicht einfach die Computer-ID abgleichen. Stattdessen wird die dem Computer während der Individualisierung zugewiesene zufällige Computer-GUID angewendet.
