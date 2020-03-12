---
description: 'null'
seo-description: 'null'
seo-title: Identitätsbasierte Domänenregistrierungslogik
title: Identitätsbasierte Domänenregistrierungslogik
uuid: bc13f7c2-9a20-4f80-b96f-05f7a0fcc343
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Identitätsbasierte Domänenregistrierungslogik{#identity-based-domain-registration-logic}

## Domänenregistrierungslogik {#section_149C247458954877AF158B4A09A8526B}

Die Referenzimplementierung wendet die folgende Logik für die identitätsbasierte Domänenregistrierung an:

1. Legen Sie den Domänennamen fest, der einem bestimmten Benutzer zugewiesen werden soll.

   Der Domänenname ( `namequalifier:username`) wird aus dem Authentifizierungstoken extrahiert. Wenn kein Token verfügbar ist, wird ein Fehler ausgegeben.
1. Suchen Sie den Domänennamen in der `DomainServerInfo` Tabelle.

   Wenn kein Eintrag gefunden wird, fügen Sie einen Eintrag ein. Die Standardwerte sind:

   * `authentication required`
   * `max domain membership=5`
   .

1. So überprüfen Sie, ob das Gerät bei der Domäne registriert wurde:

   1. Suchen Sie die `domainname` Tabelle `UserDomainMembership` :

      1. Vergleichen Sie für jede Computer-ID, die sich befindet, die ID mit der Computer-ID in der Anforderung.
      1. Wenn es sich um einen neuen Computer handelt, fügen Sie der `UserDomainMembership` Tabelle einen Eintrag hinzu.
      1. Suchen Sie nach den passenden Datensätzen in der `UserDomainRefCount` Tabelle.
      1. Wenn für diese Computer-GUID kein Eintrag vorhanden ist, fügen Sie einen Datensatz hinzu.
   1. Wenn es sich um ein neues Gerät handelt und der `Max Membership` Wert erreicht wurde, wird der Fehler zurückgegeben.


1. Suchen Sie alle Domänenschlüssel für diese Domäne in der `DomainKeys` Tabelle:

   1. Wenn `DomainServerInfo` dies bedeutet, dass ein Rollover der Schlüssel erforderlich ist, erstellen Sie ein neues Schlüsselpaar.
   1. Speichern Sie das Paar in der `DomainKeys` Tabelle mit einer Schlüsselversion, die einen höheren Wert hat als der höchste vorhandene Schlüssel.
   1. Setzen Sie die `Key Rollover Required` Markierung zurück in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domänenderegistrierungslogik {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

Die Referenz-Implementierung wendet die folgende Logik für die identitätsbasierte Domänenderegistrierung an:

1. Legen Sie den Domänennamen fest, der diesem Benutzer zugewiesen werden soll.

   Der Domänenname wird `namequalifier:username`aus dem Authentifizierungstoken extrahiert. Wenn kein Token verfügbar ist, wird der Fehler zurückgegeben `DOM_AUTHENTICATION_REQUIRED (503)` .
1. Suchen Sie den gewünschten Domänennamen in der `DomainServerInfo` Tabelle.
1. Suchen Sie den Domänennamen in der `UserDomainMembership` Tabelle.
1. Vergleichen Sie jede Computer-ID, die Sie finden, mit der Computer-ID in der Anforderung.
1. Suchen Sie den entsprechenden Eintrag in der `UserDomainRefCount` Tabelle.

   Wenn sich kein übereinstimmender Eintrag befindet, wird der Fehler zurückgegeben.

1. Wenn dies keine Vorschau ist, löschen Sie den Eintrag aus der `UserDomainRefCount` Tabelle.
1. Wenn keine weiteren Einträge in der Tabelle für den Computer vorhanden sind, löschen Sie den Eintrag aus `UserDomainMembership` und legen Sie das [!DNL Key Rollover Required] Flag in der `DomainServerInfo` -Eigenschaft fest.

Jeder Benutzer kann eine kleine Anzahl von Computern registrieren, sodass Sie die vollständige Computer-ID und die `matches()` Methode zum Zählen von Computern verwenden können. Da sich ein Benutzer mehrmals über mehrere AIR-Anwendungen oder Player in verschiedenen Browsern registrieren kann, muss der Server eine Referenz-Anzahl beibehalten, damit auch die Deregistrierung gezählt werden kann.

>[!NOTE]
>
>Die Aufhebung der Registrierung ist erst dann abgeschlossen, wenn alle Domänentoken auf dem Computer zurückgegeben wurden.

