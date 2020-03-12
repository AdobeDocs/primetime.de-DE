---
seo-title: Arbeiten mit Listen zur Richtlinienaktualisierung
title: Arbeiten mit Listen zur Richtlinienaktualisierung
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Arbeiten mit Listen zur Richtlinienaktualisierung{#working-with-policy-update-lists}

Bei Lizenzservern, die keinen Zugriff auf eine Datenbank zum Speichern von Informationen zu Richtlinien haben, können Sie eine Liste zur Richtlinienaktualisierung verwenden, um den Lizenzserver über aktualisierte Richtlinien zu informieren. Listen zur Richtlinienaktualisierung können aktualisierte Versionen von Richtlinien oder eine Liste von Richtlinien-IDs enthalten, die widerrufen wurden. Wenn eine Liste zur Richtlinienaktualisierung in bereitgestellt wird, `HandlerConfiguration`erzwingt das SDK diese Liste bei der Lizenzerteilung.

Richtlinien können auch widerrufen werden, wenn Inhaltsinhaber oder -händler die Erteilung von Lizenzen im Rahmen einer bestimmten Richtlinie einstellen möchten. Eine Liste zur Richtlinienaktualisierung kann verwendet werden, um Richtliniensperrungen im SDK zu erzwingen. Listen zur Richtlinienaktualisierung können auch verwendet werden, um eine Liste aktualisierter Richtlinien für das SDK bereitzustellen. Beachten Sie, dass beim Widerrufen einer Richtlinie keine bereits erteilten Lizenzen widerrufen werden. Sie verhindert nur, dass im Rahmen dieser Politik zusätzliche Lizenzen erteilt werden.

Beim Arbeiten mit Listen zur Richtlinienaktualisierung wird ein `PolicyUpdateListFactory` Objekt verwendet. Um eine Liste zur Richtlinienaktualisierung zu erstellen, laden Sie eine vorhandene Liste zur Richtlinienaktualisierung und überprüfen Sie, ob eine Richtlinie mithilfe der Java-API aktualisiert oder gesperrt wurde:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredentialFactory` Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `PolicyUpdateListFactory` Instanz mit der `ServerCredential` , die Sie erstellt haben.
1. Geben Sie die Richtlinien-ID an, die gesperrt werden soll.
1. Erstellen Sie ein `PolicyRevocationEntry` Objekt mit der soeben erstellten Richtlinien-ID und fügen Sie es der Liste zur Richtlinienaktualisierung hinzu, indem Sie es an übergeben `String` `PolicyUpdateListFactory.addRevocationEntry()`. Generieren Sie die neue Liste zur Richtlinienaktualisierung durch Aufruf `PolicyUpdateListFactory.generatePolicyUpdateList()`. Auf ähnliche Weise können der Liste aktualisierte Richtlinien mit `PolicyUpdateEntry`hinzugefügt werden.
1. Wenn bereits eine Liste zur Richtlinienaktualisierung vorhanden ist, können Sie sie durch Aufruf serialisieren `PolicyUpdateList.getBytes()`. Rufen Sie zum Laden der Liste die serialisierte Liste auf `PolicyUpdateListFactory.loadPolicyUpdateList()` und übergeben Sie sie.
1. Vergewissern Sie sich, dass die Signatur gültig ist und die Liste durch Aufruf des korrekten Lizenzserverzertifikats signiert wurde `PolicyUpdateList.verifySignature()`.
1. Um zu überprüfen, ob ein Eintrag gesperrt wurde, übergeben Sie die Richtlinien-ID `String` an `PolicyUpdateList.isRevoked()`. Alternativ kann die Liste weitergegeben werden `HandlerConfiguration` und wird bei der Erteilung der Lizenzen durchgesetzt.

Um einer vorhandenen Liste weitere Einträge hinzuzufügen, laden Sie eine vorhandene  zur Richtlinienaktualisierung. `PolicyUpdateList` Erstellen Sie eine neue `PolicyUpdateListFactory` Instanz. Rufen Sie P `olicyUpdateListFactory.addEntries` auf, um alle Einträge aus der alten Liste der neuen Liste hinzuzufügen. Rufen Sie `PolicyUpdateListFactory.addRevocationEntry` oder `addUpdatedEntry` fügen Sie der PolicyUpdateList neue Sperrungs- oder Aktualisierungseinträge hinzu.

Beispielcode zum Erstellen einer Liste zur Richtlinienaktualisierung, Laden einer vorhandenen Liste zur Richtlinienaktualisierung und Überprüfen, ob eine Richtlinie widerrufen wurde, finden Sie unter &quot;Beispiele&quot; `com.adobe.flashaccess.samples.policyupdatelist` im Verzeichnis der Tools für die Referenzimplementierungs-Befehlszeile `.CreatePolicyUpdateList` .
