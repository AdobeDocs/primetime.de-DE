---
seo-title: Identitätsbasierte Domänen
title: Identitätsbasierte Domänen
uuid: 34cad19b-1adb-4e0c-ac59-50632f6988f7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Identitätsbasierte Domänen {#identity-based-domains}

In diesem Fall verfügt jeder authentifizierte Benutzer über eine eigene Domäne und eine bestimmte Anzahl von Geräten kann der Domäne beitreten. Um diesen Domänentyp mit der Referenz-Implementierung zu verwenden, erstellen Sie eine Richtlinie, die die Domänenregistrierung angibt. Geben Sie den Host und Anschluss des Servers für die URL des Domänenservers an und geben Sie die erforderliche Authentifizierung mit Benutzername und Kennwort an.

Die Referenzimplementierung implementiert die folgende Logik für die Domänenregistrierung:

1. Legen Sie den Domänennamen fest, der diesem Benutzer zugewiesen werden soll. Der Domänenname wird mit * `namequalifier:username`* aus dem Authentifizierungstoken extrahiert. Wenn kein Authentifizierungstoken vorhanden ist, geben Sie den Fehler DOM_AUTHENTICATION_REQUIRED (503) zurück.
1. Suchen Sie den Domänennamen in der Tabelle `DomainServerInfo`. Wenn ein Eintrag nicht gefunden wird, fügen Sie einen Eintrag in die Tabelle ein (Standardwerte sind Authentifizierung erforderlich, max. Domänenmitgliedschaft=5).
1. Überprüfen Sie, ob das Gerät bereits bei der Domäne registriert ist:

   1. Suchen Sie den Domänennamen in der Tabelle `UserDomainMembership`. Vergleichen Sie für jede gefundene Computer-ID mit der Computer-ID in der Anforderung. Wenn dies ein neuer Computer ist, fügen Sie der Tabelle `UserDomainMembership` einen Eintrag hinzu. Suchen Sie dann die passenden Datensätze in der Tabelle `UserDomainRefCount`. Wenn für diese Computer-GUID kein Eintrag vorhanden ist, fügen Sie einen Datensatz hinzu.

   1. Wenn es sich um ein neues Gerät handelt und die maximale Mitgliedschaft bereits erreicht wurde, geben Sie den Fehler DOM_LIMIT_REACHED (502) zurück.

1. Suchen Sie alle Domänenschlüssel für diese Domäne in der Tabelle &quot;DomainKeys&quot;.

   1. Wenn `DomainServerInfo` angibt, dass die Schlüssel aktualisiert werden müssen, erstellen Sie ein neues Schlüsselpaar, speichern Sie es in der Tabelle `DomainKeys` (mit einer Schlüsselversion höher als der höchste vorhandene Schlüssel) und setzen Sie das Flag &quot;Key Rollover Erforderlich&quot;in `DomainServerInfo` zurück.

   1. Generieren Sie für jeden Domänenschlüssel eine Domänenberechtigung.

Bei der Referenzimplementierung wird die folgende Logik für die Domänenderegistrierung implementiert:

1. Legen Sie den Domänennamen fest, der diesem Benutzer zugewiesen werden soll. Der Domänenname wird aus dem Authentifizierungstoken extrahiert. ** Wenn kein Authentifizierungstoken vorhanden ist, geben Sie den Fehler DOM_AUTHENTICATION_REQUIRED (503) zurück.
1. Suchen Sie den angeforderten Domänennamen in der Tabelle `DomainServerInfo`.
1. Suchen Sie den Domänennamen in der Tabelle `UserDomainMembership`. Vergleichen Sie für jede gefundene Computer-ID mit der Computer-ID in der Anforderung. Suchen Sie den entsprechenden Eintrag in der Tabelle `UserDomainRefCount`. Wenn kein übereinstimmender Eintrag gefunden wird, geben Sie den Fehler DEREG_DENIED (401) zurück.

1. Wenn dies keine Anforderung zur Vorschau ist, löschen Sie den Eintrag aus der Tabelle `UserDomainRefCount`. Wenn keine weiteren Einträge in der Tabelle für den Computer vorhanden sind, löschen Sie den Eintrag aus `UserDomainMembership` und setzen Sie das Flag &quot;Key Rollover Required&quot;in `DomainServerInfo`.

In diesem Anwendungsfall ist es jedem Benutzer erlaubt, eine kleine Anzahl von Computern zu registrieren, sodass wir die vollständige Computer-ID und die `matches()`-Methode verwenden können, um Maschinen genau zu zählen. Da der Benutzer sich jedoch mehrmals auf diesem Computer registrieren kann (über mehrere AIR-Anwendungen oder Player in verschiedenen Browsern), muss der Server auch eine Referenz-Anzahl beibehalten, damit die Deregistrierung genau gezählt werden kann. Die Deregistrierung kann nicht als abgeschlossen betrachtet werden, bis alle Domänentoken auf dem Computer zurückgegeben werden.
