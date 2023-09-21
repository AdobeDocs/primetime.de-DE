---
title: Sperren von Anmeldeinformationen des Computers
description: Sperren von Anmeldeinformationen des Computers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Sperren von Anmeldeinformationen des Computers{#revoking-machine-credentials}

Adobe unterhält eine Zertifikatsperrliste für das Sperren von Anmeldeinformationen von Computern, von denen bekannt ist, dass sie beeinträchtigt sind. Diese Zertifikatsperrliste wird automatisch vom SDK erzwungen. Wenn es zusätzliche Computer gibt, für die Ihr Lizenzserver keine Lizenzen ausstellen soll, können Sie eine Liste für die Sperrung von Computern erstellen und den Namen des Ausstellers und die Seriennummer der Computer-Token hinzufügen, die Sie ausschließen möchten (verwenden Sie `MachineToken.getMachineTokenId()` um den Namen des Ausstellers und die Seriennummer des Maschinenzertifikats abzurufen).

Das Sperren von Anmeldeinformationen für den Computer umfasst die Verwendung eines `RevocationListFactory` -Objekt. Um eine Sperrliste zu erstellen, eine vorhandene Sperrliste zu laden und zu überprüfen, ob ein Computer-Token mithilfe der Java-API gesperrt wurde, führen Sie die folgenden Schritte aus:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die in [Einrichten der Entwicklungsumgebung](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in Ihrem Projekt.
1. Erstellen Sie eine `ServerCredentialFactory` -Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden. Die Berechtigung für den Lizenzserver wird zum Signieren der Sperrliste verwendet.
1. Erstellen Sie eine `RevocationListFactory` -Instanz.
1. Geben Sie den Aussteller und die Seriennummer des zu widerrufenden Computer-Tokens mithilfe eines `IssuerAndSerialNumber` -Objekt. Alle Adobe Access-Anfragen enthalten ein Computer-Token.
1. Erstellen Sie eine `RevocationList` -Objekt, das `IssuerAndSerialNumber` -Objekt, das Sie gerade erstellt haben, und fügen Sie es der Sperrliste hinzu, indem Sie es an `RevocationListFactory.addRevocationEntry()`. Generieren Sie die neue Sperrliste durch Aufruf von `RevocationListFactory.generateRevocationList()`.
1. Um die Sperrliste zu speichern, können Sie sie serialisieren, indem Sie `RevocationList.getBytes()`. Um die Liste zu laden, rufen Sie `RevocationListFactory.loadRevocationList()` und übergeben Sie die serialisierte Liste.
1. Stellen Sie sicher, dass die Signatur gültig ist und die Liste vom richtigen Lizenzserver signiert wurde, indem Sie `RevocationList.verifySignature()`.
1. Um zu überprüfen, ob ein Eintrag widerrufen wurde, übergeben Sie die `IssuerAndSerialNumber` Objekt in `RevocationList.isRevoked()`. Die Sperrliste kann auch an `HandlerConfiguration` , damit das SDK die Sperrliste für alle Authentifizierungs- und Lizenzanfragen erzwingt.

So fügen Sie einem vorhandenen Eintrag zusätzliche Einträge hinzu `RevocationList`, laden Sie eine vorhandene Sperrliste. Erstellen Sie eine neue `RevocationListFactory` und stellen Sie sicher, dass Sie die Zertifikatsperrlisten-Nummer erhöhen. Aufruf `RevocationListFactioryEntries.addRevocationEntries` , um alle Einträge aus der alten Liste der neuen Liste hinzuzufügen. Aufruf `RevocationListFactory.addRevocationEntry` , um der RevocationList alle neuen Sperreinträge hinzuzufügen.

Beispielcode, der veranschaulicht, wie eine Sperrliste erstellt wird, eine vorhandene Sperrliste lädt und überprüft, ob ein Computer-Token gesperrt wurde, finden Sie unter `com.adobe.flashaccess.samples.revocation.CreateRevocationList` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
