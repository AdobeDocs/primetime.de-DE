---
title: Arbeiten mit Listen für Richtlinienaktualisierungen
description: Arbeiten mit Listen für Richtlinienaktualisierungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Arbeiten mit Listen für Richtlinienaktualisierungen{#working-with-policy-update-lists}

Bei Lizenzservern, die keinen Zugriff auf eine Datenbank zum Speichern von Informationen zu Richtlinien haben, können Sie eine Liste mit Richtlinienaktualisierungen verwenden, um den Lizenzserver über aktualisierte Richtlinien zu informieren. Listen für Richtlinienaktualisierungen können aktualisierte Versionen von Richtlinien oder eine Liste von Richtlinien-IDs enthalten, die widerrufen wurden. Wenn eine Liste mit Richtlinienaktualisierungen in `HandlerConfiguration`festgelegt ist, setzt das SDK diese Liste bei der Lizenzerteilung um.

Richtlinien können auch widerrufen werden, wenn Inhaber oder Händler von Inhalten die Erteilung von Lizenzen im Rahmen einer bestimmten Richtlinie einstellen möchten. Eine Liste mit Richtlinienaktualisierungen kann verwendet werden, um die Sperrung von Richtlinien im SDK zu erzwingen. Über Listen zur Richtlinienaktualisierung kann auch eine Liste aktualisierter Richtlinien für das SDK bereitgestellt werden. Beachten Sie, dass durch die Aufhebung einer Richtlinie bereits erteilte Lizenzen nicht widerrufen werden. Sie verhindert nur, dass zusätzliche Lizenzen im Rahmen dieser Politik erteilt werden.

Das Arbeiten mit Listen zur Aktualisierung von Richtlinien umfasst die Verwendung einer `PolicyUpdateListFactory` -Objekt. Um eine Liste mit Richtlinienaktualisierungen zu erstellen, laden Sie eine vorhandene Liste mit Richtlinienaktualisierungen und überprüfen Sie, ob eine Richtlinie mithilfe der Java-API aktualisiert oder widerrufen wurde:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die unter Einrichten der Entwicklungsumgebung in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredentialFactory` -Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `PolicyUpdateListFactory` -Instanz mit der `ServerCredential` haben Sie erstellt.
1. Geben Sie die Richtlinien-ID an, die gesperrt werden soll.
1. Erstellen Sie eine `PolicyRevocationEntry` Objekt, das die Richtlinien-ID verwendet `String` Sie haben die Richtlinie gerade erstellt und zur Liste der aktualisierten Richtlinien hinzugefügt, indem Sie sie an `PolicyUpdateListFactory.addRevocationEntry()`. Generieren Sie die neue Richtlinienaktualisierungsliste durch Aufruf von `PolicyUpdateListFactory.generatePolicyUpdateList()`. Ebenso können aktualisierte Richtlinien zur Liste hinzugefügt werden, indem `PolicyUpdateEntry`.
1. Wenn bereits eine Liste mit Richtlinienaktualisierungen vorhanden ist, können Sie sie für das Laden serialisieren, indem Sie `PolicyUpdateList.getBytes()`. Um die Liste zu laden, rufen Sie `PolicyUpdateListFactory.loadPolicyUpdateList()` und übergeben Sie die serialisierte Liste.
1. Überprüfen Sie, ob die Signatur gültig ist und ob die Liste vom richtigen Lizenzserver-Zertifikat signiert wurde, indem Sie `PolicyUpdateList.verifySignature()`.
1. Übergeben Sie die Richtlinien-ID, um zu überprüfen, ob ein Eintrag widerrufen wurde. `String` in `PolicyUpdateList.isRevoked()`. Alternativ kann die Liste an `HandlerConfiguration` und wird bei der Erteilung der Lizenzen durchgesetzt.

So fügen Sie einem vorhandenen Eintrag zusätzliche Einträge hinzu `PolicyUpdateList`, laden Sie eine vorhandene Liste mit Richtlinienaktualisierungen. Erstellen Sie eine neue `PolicyUpdateListFactory` -Instanz. Aufruf P `olicyUpdateListFactory.addEntries` , um alle Einträge aus der alten Liste der neuen Liste hinzuzufügen. Aufruf `PolicyUpdateListFactory.addRevocationEntry` oder `addUpdatedEntry` , um der PolicyUpdateList neue Sperren oder Aktualisierungseinträge hinzuzufügen.

Beispielcode, der zeigt, wie eine Liste mit Richtlinienaktualisierungen erstellt wird, eine vorhandene Liste mit Richtlinienaktualisierungen lädt und überprüft, ob eine Richtlinie widerrufen wurde, finden Sie unter `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
