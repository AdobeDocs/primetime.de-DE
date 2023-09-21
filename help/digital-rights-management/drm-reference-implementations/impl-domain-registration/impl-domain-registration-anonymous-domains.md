---
title: Anonyme Domain-Logik
description: Anonyme Domain-Logik
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Anonyme Domain-Logik{#anonymous-domain-logic}

## Domain-Registrierungslogik {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

Die Referenzimplementierung wendet die folgende Logik für die Registrierung anonymer Domänen an:

1. Analysieren Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie nach dem Domänennamen im `DomainServerInfo` Tabelle.
1. Wenn Sie einen Eintrag nicht finden können, fügen Sie einen Eintrag in die Tabelle ein.

   Die Standardwerte sind:

   * `authentication is not required`
   * `no membership maximum`

   Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anfrage ein gültiges Authentifizierungstoken enthalten ist. Wenn der Auth-Namespace in der Datenbank angegeben ist, muss das Token mit dem angegebenen Auth-Namespace übereinstimmen.
1. Wenn eine Authentifizierung erforderlich ist, aber kein gültiges Authentifizierungstoken verfügbar ist, geben Sie einen Fehler zurück. `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Überprüfen Sie, ob das Gerät bei der Domäne registriert ist:

   1. Suchen Sie nach dem Domänennamen im `DomainMembership` Tabelle.
   1. Vergleichen Sie die maschinelle GUID, die Sie in der Anfrage mit der GUID des Computers finden.
   1. Wenn es sich um einen neuen Computer handelt, fügen Sie einen Eintrag im `DomainMembership` Tabelle.
   1. Wenn es ein neues Gerät ist und `Max Membership` Wert erreicht wurde, Fehler zurückgeben `DOM_LIMIT_REACHED (502)`.

1. Suchen Sie alle Domain-Schlüssel für diese Domäne im `DomainKeys` table:

   1. Wenn `DomainServerInfo` gibt an, dass die Schlüssel umgerollt werden müssen, und generiert ein neues Schlüsselpaar.
   1. Speichern Sie die Tastatur im `DomainKeys` mit einer Schlüsselversion, die eine Zahl höher als der höchste vorhandene Schlüssel ist.
   1. Setzen Sie die `Key Rollover Required` Markierung in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domain-Deregistrierungslogik {#section_C968BBFCBFAB4510A903D169F38C9FCE}

Die Referenzimplementierung wendet die folgende Logik für die Deregistrierung einer anonymen Domäne an:

1. Analysieren Sie den Domänennamen aus der Anforderungs-URL.
1. Suchen Sie nach dem angeforderten Domänennamen im `DomainServerInfo` Tabelle.
1. Wenn für die angeforderte Domäne eine Authentifizierung erforderlich ist, stellen Sie sicher, dass in der Anfrage ein gültiges Authentifizierungstoken enthalten ist.

   Das Token muss auch mit dem Auth-Namespace übereinstimmen, der in der Datenbank angegeben ist.
1. Suchen Sie nach dem Domänennamen und der GUID des Computers im `DomainMembership` Tabelle.

   Wenn Sie einen übereinstimmenden Eintrag nicht finden können, geben Sie einen Fehler zurück. `DEREG_DENIED (401)`.

1. Wenn es sich nicht um eine Vorschauanfrage handelt, löschen Sie den Eintrag aus `DomainMembership`und in `DomainServerInfo`, legen Sie die `Key Rollover Required` Markierung.

Da viele Computer der Domäne beitreten können, können Sie nicht einfach die Computer-ID abgleichen. Stattdessen wird die zufällige maschinelle GUID angewendet, die der Maschine während der Individualisierung zugewiesen wird.
