---
title: Identitätsbasierte Domänen
description: Identitätsbasierte Domänen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Identitätsbasierte Domänen {#identity-based-domains}

In diesem Anwendungsfall hat jeder authentifizierte Benutzer seine eigene Domäne und eine bestimmte Anzahl von Geräten darf der Domäne beitreten. Um diesen Domänentyp mit der Referenzimplementierung zu verwenden, erstellen Sie eine Richtlinie, die die Domänenregistrierung angibt. Geben Sie den Host und Port Ihres Servers für die URL des Domänenservers an und geben Sie die Authentifizierung mit Benutzername/Kennwort an.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenregistrierung:

1. Bestimmen Sie den Domänennamen, der diesem Benutzer zugewiesen werden soll. Der Domänenname lautet * `namequalifier:username`* aus dem Authentifizierungstoken extrahiert. Wenn kein Authentifizierungstoken vorhanden ist, geben Sie den Fehler DOM_AUTHENTICATION_REQUIRED (503) zurück.
1. Suchen Sie den Domänennamen im `DomainServerInfo` Tabelle. Wenn kein Eintrag gefunden wird, fügen Sie einen Eintrag in die Tabelle ein (Standardwerte sind Authentifizierung erforderlich, max domain membership=5).
1. Überprüfen Sie, ob das Gerät bereits bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen im `UserDomainMembership` Tabelle. Vergleichen Sie für jede gefundene Computer-ID mit der Computer-ID in der Anfrage. Wenn es sich um einen neuen Computer handelt, fügen Sie dem `UserDomainMembership` Tabelle. Suchen Sie dann die entsprechenden Datensätze in `UserDomainRefCount` Tabelle. Wenn für diese maschinelle GUID kein Eintrag vorhanden ist, fügen Sie einen Datensatz hinzu.

   1. Wenn es sich um ein neues Gerät handelt und die Max-Mitgliedschaft bereits erreicht wurde, geben Sie den Fehler DOM_LIMIT_REACHED (502) zurück.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der Tabelle DomainKeys .

   1. Wenn `DomainServerInfo` gibt an, dass die Schlüssel umgerollt werden müssen, ein neues Schlüsselpaar generieren und es im `DomainKeys` -Tabelle (mit Schlüsselversion 1 höher als der höchste vorhandene Schlüssel) und setzen Sie das Flag &quot;Schlüsselaktualisierung erforderlich&quot;in `DomainServerInfo`.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenderegistrierung:

1. Bestimmen Sie den Domänennamen, der diesem Benutzer zugewiesen werden soll. Der Domänenname lautet *namequalifier:Benutzername* aus dem Authentifizierungstoken extrahiert. Wenn kein Authentifizierungstoken vorhanden ist, geben Sie den Fehler DOM_AUTHENTICATION_REQUIRED (503) zurück.
1. Suchen Sie den angeforderten Domänennamen im `DomainServerInfo` Tabelle.
1. Suchen Sie den Domänennamen im `UserDomainMembership` Tabelle. Vergleichen Sie für jede gefundene Computer-ID mit der Computer-ID in der Anfrage. Suchen Sie den entsprechenden Eintrag im `UserDomainRefCount` Tabelle. Wenn kein übereinstimmender Eintrag gefunden wird, wird der Fehler DEREG_DENIED (401) zurückgegeben.

1. Wenn es sich nicht um eine Vorschauanfrage handelt, löschen Sie den Eintrag aus `UserDomainRefCount` Tabelle. Wenn die Tabelle keine Einträge mehr für den Computer enthält, löschen Sie den Eintrag aus `UserDomainMembership` und legen Sie die Markierung &quot;Key Rollover Required&quot;in `DomainServerInfo`.

In diesem Anwendungsfall darf jeder Benutzer eine kleine Anzahl von Computern registrieren, sodass wir die vollständige Computer-ID und die `matches()` -Methode, um Maschinen genau zu zählen. Da sich der Benutzer jedoch mehrmals auf diesem Computer registrieren kann (über mehrere AIR-Anwendungen oder Player in verschiedenen Browsern), muss der Server auch eine Referenzanzahl beibehalten, damit die Abmeldung korrekt gezählt werden kann. Die Deregistrierung kann erst als abgeschlossen betrachtet werden, wenn alle Domänen-Token auf dem Computer zurückgegeben wurden.
