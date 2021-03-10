---
title: Identitätsbasierte Domänenregistrierungslogik
description: Identitätsbasierte Domänenregistrierungslogik
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Identitätsbasierte Domänenregistrierungslogik{#identity-based-domain-registration-logic}

## Domänenregistrierungslogik {#section_149C247458954877AF158B4A09A8526B}

Die Referenzimplementierung wendet die folgende Logik für die identitätsbasierte Domänenregistrierung an:

1. Legen Sie den Domänennamen fest, der einem bestimmten Benutzer zugewiesen werden soll.

   Der Domänenname ( `namequalifier:username`) wird aus dem Authentifizierungstoken extrahiert. Wenn kein Token verfügbar ist, wird ein Fehler ausgegeben.
1. Suchen Sie den Domänennamen in der Tabelle `DomainServerInfo`.

   Wenn kein Eintrag gefunden wird, fügen Sie einen Eintrag ein. Die Standardwerte sind:

   * `authentication required`
   * `max domain membership=5`

   .

1. So überprüfen Sie, ob das Gerät bei der Domäne registriert wurde:

   1. Suchen Sie in der Tabelle `UserDomainMembership` nach `domainname`:

      1. Vergleichen Sie für jede Computer-ID, die sich befindet, die ID mit der Computer-ID in der Anforderung.
      1. Wenn dies ein neuer Computer ist, fügen Sie der Tabelle `UserDomainMembership` einen Eintrag hinzu.
      1. Suchen Sie in der Tabelle `UserDomainRefCount` nach den entsprechenden Datensätzen.
      1. Wenn für diese Computer-GUID kein Eintrag vorhanden ist, fügen Sie einen Datensatz hinzu.
   1. Wenn es sich um ein neues Gerät handelt und der Wert `Max Membership` erreicht wurde, wird der Fehler zurückgegeben.


1. Suchen Sie alle Domänenschlüssel für diese Domäne in der Tabelle `DomainKeys`:

   1. Wenn `DomainServerInfo` angibt, dass ein Rollover der Schlüssel erforderlich ist, erstellen Sie ein neues Schlüsselpaar,
   1. Speichern Sie das Paar in der Tabelle `DomainKeys` mit einer Schlüsselversion, die höher als der höchste vorhandene Schlüssel ist.
   1. Setzen Sie das `Key Rollover Required`-Flag in `DomainServerInfo` zurück.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

## Domänenderegistrierungslogik {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

Die Referenz-Implementierung wendet die folgende Logik für die identitätsbasierte Domänenderegistrierung an:

1. Legen Sie den Domänennamen fest, der diesem Benutzer zugewiesen werden soll.

   Der Domänenname ist `namequalifier:username`, der aus dem Authentifizierungstoken extrahiert wird. Ist kein Token verfügbar, wird der Fehler `DOM_AUTHENTICATION_REQUIRED (503)` zurückgegeben.
1. Suchen Sie den gewünschten Domänennamen in der Tabelle `DomainServerInfo`.
1. Suchen Sie den Domänennamen in der Tabelle `UserDomainMembership`.
1. Vergleichen Sie jede Computer-ID, die Sie finden, mit der Computer-ID in der Anforderung.
1. Suchen Sie den entsprechenden Eintrag in der Tabelle `UserDomainRefCount`.

   Wenn sich kein übereinstimmender Eintrag befindet, wird der Fehler zurückgegeben.

1. Wenn dies keine Anforderung zur Vorschau ist, löschen Sie den Eintrag aus der Tabelle `UserDomainRefCount`.
1. Wenn keine weiteren Einträge in der Tabelle für den Computer vorhanden sind, löschen Sie den Eintrag aus `UserDomainMembership` und setzen Sie das [!DNL Key Rollover Required]-Flag in der `DomainServerInfo`-Eigenschaft.

Jeder Benutzer kann eine kleine Anzahl von Computern registrieren, sodass Sie zum Zählen von Computern die vollständige Computer-ID und die `matches()`-Methode verwenden können. Da sich ein Benutzer mehrmals über mehrere AIR-Anwendungen oder Player in verschiedenen Browsern registrieren kann, muss der Server eine Referenz-Anzahl beibehalten, damit auch die Deregistrierung gezählt werden kann.

>[!NOTE]
>
>Die Aufhebung der Registrierung ist erst dann abgeschlossen, wenn alle Domänentoken auf dem Computer zurückgegeben wurden.

