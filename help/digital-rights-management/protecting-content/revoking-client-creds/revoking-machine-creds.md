---
title: Sperren von Computeranmeldeinformationen
description: Sperren von Computeranmeldeinformationen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Sperren der Anmeldeinformationen des Computers {#revoking-machine-credentials}

Adobe unterhält eine Zertifikatsperrliste zum Sperren von Computerberechtigungen, die bekanntermaßen beeinträchtigt sind. Diese Zertifikatsperrliste wird automatisch vom SDK erzwungen. Wenn es zusätzliche Computer gibt, auf denen Ihr Lizenzserver keine Lizenzen ausstellen soll, können Sie eine Liste zum Zurücknehmen des Computers erstellen und den Namen des Ausstellers und die Seriennummer der auszuschließenden Gerätetoken hinzufügen (verwenden Sie `MachineToken.getMachineTokenId()`, um den Ausstellernamen und die Seriennummer des Computerzertifikats abzurufen).

Beim Sperren von Anmeldeinformationen für den Computer wird ein `RevocationListFactory`-Objekt verwendet. Um eine Liste zum Sperren zu erstellen, laden Sie eine vorhandene Liste zum Sperren und überprüfen Sie, ob ein Computertoken mithilfe der Java-API gesperrt wurde:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die unter [Einrichten der Development-Umgebung](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) in Ihrem Projekt erwähnt werden.
1. Erstellen Sie eine `ServerCredentialFactory`-Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden. Die Berechtigung für den Lizenzserver wird zum Signieren der Liste für den Widerruf verwendet.
1. Erstellen Sie eine `RevocationListFactory`-Instanz.
1. Geben Sie den Aussteller und die Seriennummer des Computertokens an, das mit einem `IssuerAndSerialNumber`-Objekt gesperrt werden soll. Alle Adobe Primetime DRM-Anforderungen enthalten ein Computer-Token.
1. Erstellen Sie ein `RevocationList`-Objekt mit dem zuvor erstellten `IssuerAndSerialNumber`-Objekt und fügen Sie es der Liste zum Sperren hinzu, indem Sie es an `RevocationListFactory.addRevocationEntry()` übergeben. Generieren Sie die neue Liste zum Sperren, indem Sie `RevocationListFactory.generateRevocationList()` aufrufen.

1. Um die Liste zum Sperren zu speichern, können Sie sie serialisieren, indem Sie `RevocationList.getBytes()` aufrufen. Rufen Sie zum Laden der Liste `RevocationListFactory.loadRevocationList()` auf und geben Sie die serialisierte Liste ein.

1. Vergewissern Sie sich, dass die Signatur gültig ist und die Liste vom richtigen Lizenzserver durch Aufruf von `RevocationList.verifySignature()` signiert wurde.
1. Um zu überprüfen, ob ein Eintrag gesperrt wurde, übergeben Sie das `IssuerAndSerialNumber`-Objekt an `RevocationList.isRevoked()`. Die Liste zum Widerruf kann auch an `HandlerConfiguration` übergeben werden, damit das SDK die Liste zum Widerruf für alle Authentifizierungs- und Lizenzanforderungen erzwingt.

Um einer vorhandenen `RevocationList` weitere Einträge hinzuzufügen, laden Sie eine vorhandene Liste zum Sperren. Erstellen Sie eine neue Instanz `RevocationListFactory` und stellen Sie sicher, dass Sie die Zertifikatsperrlisten-Nummer erhöhen. Rufen Sie `RevocationListFactioryEntries.addRevocationEntries` auf, um der neuen Liste alle Einträge aus der alten Liste hinzuzufügen. Rufen Sie `RevocationListFactory.addRevocationEntry` auf, um der RevocationList alle neuen Sperreinträge hinzuzufügen.

Beispielcode zum Erstellen einer Liste zum Sperren, Laden einer vorhandenen Liste zum Sperren und Überprüfen, ob ein Computertoken gesperrt wurde, finden Sie unter `com.adobe.flashaccess.samples.revocation.CreateRevocationList` im Ordner [!DNL samples] der Befehlszeilenwerkzeuge für die Referenzimplementierung .
