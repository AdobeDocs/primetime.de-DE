---
description: 'null'
seo-description: 'null'
seo-title: Anonyme Domänenlogik
title: Anonyme Domänenlogik
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Anonyme Domänenlogik{#anonymous-domain-logic}

## Domänenregistrierungslogik {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

Die Referenzimplementierung wendet die folgende Logik für die anonyme Domänenregistrierung an:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den Domänennamen in der Tabelle `DomainServerInfo`.
1. Wenn Sie einen Eintrag nicht finden können, fügen Sie einen Eintrag in die Tabelle ein.

   Die Standardwerte sind:

   * `authentication is not required`
   * `no membership maximum`

   Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anforderung ein gültiges Authentifizierungstoken vorhanden ist. Wenn der Auth-Namensraum in der Datenbank angegeben ist, muss das Token mit dem angegebenen Auth-Namensraum übereinstimmen.
1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken verfügbar ist, geben Sie den Fehler `DOM_AUTHENTICATION_REQUIRED (503)` zurück.
1. Überprüfen Sie, ob das Gerät bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen in der Tabelle `DomainMembership`.
   1. Vergleichen Sie die GUID des Computers, die Sie in der Anforderung finden, mit der GUID des Computers.
   1. Wenn dies ein neuer Computer ist, fügen Sie einen Eintrag in der Tabelle `DomainMembership` hinzu.
   1. Wenn es sich um ein neues Gerät handelt und der Wert `Max Membership` erreicht wurde, geben Sie den Fehler `DOM_LIMIT_REACHED (502)` zurück.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der Tabelle `DomainKeys`:

   1. Wenn `DomainServerInfo` angibt, dass ein Rollover der Schlüssel erforderlich ist, erstellen Sie ein neues Schlüsselpaar.
   1. Speichern Sie die Tastenkombination in der Tabelle `DomainKeys` mit einer Schlüsselversion, die eine Zahl höher ist als der höchste vorhandene Schlüssel.
   1. Setzen Sie das `Key Rollover Required`-Flag in `DomainServerInfo` zurück.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domänenderegistrierungslogik {#section_C968BBFCBFAB4510A903D169F38C9FCE}

Die Referenzimplementierung wendet die folgende Logik für die anonyme Domänenderegistrierung an:

1. Parsen Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie den gewünschten Domänennamen in der Tabelle `DomainServerInfo`.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anforderung ein gültiges Authentifizierungstoken vorhanden ist.

   Das Token muss auch mit dem Auth-Namensraum übereinstimmen, der in der Datenbank angegeben ist.
1. Suchen Sie den Domänennamen und die Computer-GUID in der Tabelle `DomainMembership`.

   Wenn Sie keinen übereinstimmenden Eintrag finden können, geben Sie den Fehler `DEREG_DENIED (401)` zurück.

1. Wenn dies keine Anforderung zur Vorschau ist, löschen Sie den Eintrag aus `DomainMembership` und setzen Sie in `DomainServerInfo` das `Key Rollover Required`-Flag.

Da viele Computer der Domäne beitreten können, können Sie nicht einfach die Computer-ID abgleichen. Stattdessen wird die dem Computer während der Individualisierung zugewiesene zufällige Computer-GUID angewendet.
