---
title: Identitätsbasierte Domänenregistrierungslogik
description: Identitätsbasierte Domänenregistrierungslogik
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Identitätsbasierte Domänenregistrierungslogik{#identity-based-domain-registration-logic}

## Domain-Registrierungslogik {#section_149C247458954877AF158B4A09A8526B}

Die Referenzimplementierung wendet die folgende Logik für die identitätsbasierte Domänenregistrierung an:

1. Bestimmen Sie den Domänennamen, der einem bestimmten Benutzer zugewiesen werden soll.

   Der Domänenname ( `namequalifier:username`) wird aus dem Authentifizierungstoken extrahiert. Wenn kein Token verfügbar ist, wird ein Fehler ausgegeben.
1. Suchen Sie nach dem Domänennamen im `DomainServerInfo` Tabelle.

   Wenn kein Eintrag gefunden wird, fügen Sie einen Eintrag ein. Die Standardwerte sind:

   * `authentication required`
   * `max domain membership=5`

   .

1. So überprüfen Sie, ob das Gerät bei der Domäne registriert wurde:

   1. Suchen Sie nach `domainname` im `UserDomainMembership` table:

      1. Vergleichen Sie für jede Computer-ID, die sich befindet, die ID mit der Computer-ID in der Anfrage.
      1. Wenn es sich um einen neuen Computer handelt, fügen Sie dem `UserDomainMembership` Tabelle.
      1. Suchen Sie nach übereinstimmenden Datensätzen in `UserDomainRefCount` Tabelle.
      1. Wenn für diese maschinelle GUID kein Eintrag vorhanden ist, fügen Sie einen Datensatz hinzu.

   1. Wenn es sich um ein neues Gerät handelt, wird die `Max Membership` -Wert erreicht wurde, Fehler zurückgeben .

1. Suchen Sie alle Domain-Schlüssel für diese Domäne im `DomainKeys` table:

   1. Wenn `DomainServerInfo` gibt an, dass die Schlüssel umgerollt werden müssen, und generiert ein neues Schlüsselpaar;
   1. Speichern Sie das Paar im `DomainKeys` -Tabelle mit einer Schlüsselversion, die einen höheren Wert aufweist als der höchste vorhandene Schlüssel.
   1. Setzen Sie die `Key Rollover Required` Markierung in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domain-Deregistrierungslogik {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

Die Referenzimplementierung wendet die folgende Logik für die identitätsbasierte Domänenderegistrierung an:

1. Bestimmen Sie den Domänennamen, der diesem Benutzer zugewiesen werden soll.

   Der Domänenname lautet `namequalifier:username`, der aus dem Authentifizierungstoken extrahiert wird. Wenn kein Token verfügbar ist, wird ein Fehler zurückgegeben. `DOM_AUTHENTICATION_REQUIRED (503)` auftritt.
1. Suchen Sie nach dem angeforderten Domänennamen im `DomainServerInfo` Tabelle.
1. Suchen Sie nach dem Domänennamen im `UserDomainMembership` Tabelle.
1. Vergleichen Sie die einzelnen Computer-IDs, die Sie mit der Computer-ID in der Anfrage finden.
1. Suchen Sie den entsprechenden Eintrag im `UserDomainRefCount` Tabelle.

   Wenn ein übereinstimmender Eintrag nicht gefunden wird, wird Fehler zurückgegeben.

1. Wenn es sich nicht um eine Vorschauanfrage handelt, löschen Sie den Eintrag aus dem `UserDomainRefCount` Tabelle.
1. Wenn die Tabelle keine weiteren Einträge für den Computer enthält, löschen Sie den Eintrag aus `UserDomainMembership` und legen Sie die [!DNL Key Rollover Required] -Markierung in `DomainServerInfo` -Eigenschaft.

Jeder Benutzer kann eine kleine Anzahl von Computern registrieren, sodass Sie die vollständige Computer-ID und die `matches()` Methode zum Zählen von Maschinen. Da ein Benutzer sich mehrmals über mehrere AIR-Anwendungen oder Player in verschiedenen Browsern registrieren kann, muss der Server eine Referenzanzahl beibehalten, damit auch die Abmeldung gezählt werden kann.

>[!NOTE]
>
>Die Aufhebung der Registrierung ist erst abgeschlossen, wenn alle Domänen-Token auf dem Computer ausgegeben wurden.
