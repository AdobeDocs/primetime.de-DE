---
seo-title: Sperren von Computeranmeldeinformationen
title: Sperren von Computeranmeldeinformationen
uuid: 16119ff9-8147-4fe0-9744-a705d94a9400
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Sperren von Computeranmeldeinformationen{#revoking-machine-credentials}

Adobe unterhält eine Zertifikatsperrliste zum Sperren von Computeranmeldeinformationen, die bekanntermaßen beeinträchtigt sind. Diese Zertifikatsperrliste wird automatisch vom SDK erzwungen. Wenn es zusätzliche Computer gibt, auf denen Ihr Lizenzserver keine Lizenzen ausstellen soll, können Sie eine Liste zum Zurücknehmen des Computers erstellen und den Namen des Ausstellers und die Seriennummer der auszuschließenden Gerätetoken hinzufügen (mit der Sie den Ausstellernamen und die Seriennummer des Computerzertifikats abrufen `MachineToken.getMachineTokenId()` können).

Das Sperren von Anmeldeinformationen für den Computer umfasst die Verwendung eines `RevocationListFactory` Objekts. Um eine Liste zum Sperren zu erstellen, laden Sie eine vorhandene Liste zum Sperren und überprüfen Sie, ob ein Computertoken mithilfe der Java-API gesperrt wurde:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter Einrichten der Development-Umgebung [](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredentialFactory` Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden. Die Berechtigung für den Lizenzserver wird zum Signieren der Liste für den Widerruf verwendet.
1. Erstellen Sie eine `RevocationListFactory` Instanz.
1. Geben Sie den Aussteller und die Seriennummer des Maschinentokens an, das mithilfe eines `IssuerAndSerialNumber` Objekts gesperrt werden soll. Alle Adobe Access-Anforderungen enthalten ein Computer-Token.
1. Erstellen Sie ein `RevocationList` Objekt mit dem soeben erstellten `IssuerAndSerialNumber` Objekt und fügen Sie es der Liste zum Sperren hinzu, indem Sie es an übergeben `RevocationListFactory.addRevocationEntry()`. Generieren Sie die neue Liste zum Sperren durch Aufruf `RevocationListFactory.generateRevocationList()`.
1. Um die Liste zu speichern, können Sie sie serialisieren, indem Sie sie aufrufen `RevocationList.getBytes()`. Rufen Sie zum Laden der Liste die serialisierte Liste auf `RevocationListFactory.loadRevocationList()` und übergeben Sie sie.
1. Vergewissern Sie sich, dass die Signatur gültig ist und die Liste vom korrekten Lizenzserver durch einen Aufruf signiert wurde `RevocationList.verifySignature()`.
1. Um zu überprüfen, ob ein Eintrag gesperrt wurde, übergeben Sie das `IssuerAndSerialNumber` Objekt an `RevocationList.isRevoked()`. Die Liste zum Widerruf kann auch weitergeleitet werden, `HandlerConfiguration` damit das SDK die Liste zum Widerruf für alle Authentifizierungs- und Lizenzanforderungen durchsetzen kann.

Um einer vorhandenen Liste weitere Einträge hinzuzufügen, `RevocationList`laden Sie eine vorhandene Sperre. Erstellen Sie eine neue `RevocationListFactory` Instanz und stellen Sie sicher, dass Sie die Zertifikatsperrlisten-Nummer erhöhen. Aufruf `RevocationListFactioryEntries.addRevocationEntries` zum Hinzufügen aller Einträge aus der alten Liste zur neuen Liste. Aufruf `RevocationListFactory.addRevocationEntry` zum Hinzufügen neuer Sperreinträge zur RevocationList.

Beispielcode zum Erstellen einer Revocation-Liste, Laden einer vorhandenen Revocation-Liste und Überprüfen, ob ein Maschinentoken gesperrt wurde, finden Sie `com.adobe.flashaccess.samples.revocation.CreateRevocationList` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
