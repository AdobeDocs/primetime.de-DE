---
title: Arbeiten mit DRM-Richtlinienaktualisierungslisten
description: Arbeiten mit DRM-Richtlinienaktualisierungslisten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Listen zur Aktualisierung von DRM-Richtlinien {#drm-policy-update-lists}

Wenn Sie die Nutzungsregeln in einer DRM-Richtlinie nach dem Verpacken von Inhalten aktualisieren, muss der Lizenzserver über die neueste Version verfügen, bevor er Lizenzen ausstellen kann, die eine aktualisierte DRM-Richtlinie verwenden. Eine Möglichkeit, dies zu erreichen, ist eine Liste mit aktualisierten DRM-Richtlinien.

Eine DRM-Richtlinienaktualisierungsliste wird durch eine Datei dargestellt, die eine Liste aktualisierter oder widerrufener DRM-Richtlinien enthält. Wenn Sie eine DRM-Richtlinie aktualisieren, müssen Sie eine neue DRM Policy Update List generieren und die Liste regelmäßig auf alle Lizenzserver pushen.

## Arbeiten mit DRM-Richtlinienaktualisierungslisten {#working-with-drm-policy-update-lists}

Bei Lizenzservern, die keinen Zugriff auf eine Datenbank zum Speichern von Informationen zu DRM-Richtlinien haben, können Sie eine DRM-Richtlinienaktualisierungsliste verwenden, um den Lizenzserver über aktualisierte DRM-Richtlinien zu informieren. DRM Policy Update Lists können aktualisierte Versionen von DRM-Richtlinien oder eine Liste von DRM-Richtlinien-IDs enthalten, die widerrufen wurden. Wenn eine Liste mit Richtlinienaktualisierungen in `HandlerConfiguration`, erzwingt das SDK diese Liste bei der Lizenzerteilung.

Sie können auch DRM-Richtlinien widerrufen, wenn Eigentümer oder Distributoren von Inhalten die Erteilung von Lizenzen im Rahmen einer bestimmten DRM-Richtlinie einstellen möchten. Eine DRM-Richtlinienaktualisierungsliste kann verwendet werden, um die Sperrung von DRM-Richtlinien im SDK zu erzwingen. Sie können auch DRM-Richtlinien-Aktualisierungslisten anwenden, um eine Liste aktualisierter DRM-Richtlinien für das SDK bereitzustellen.

>[!NOTE]
>
>Wenn Sie eine DRM-Richtlinie widerrufen, werden bereits erteilte Lizenzen nicht automatisch widerrufen. Sie verhindert nur, dass zusätzliche Lizenzen im Rahmen dieser DRM-Politik erteilt werden.

## Listen für Richtlinienaktualisierungen aktualisieren{#update-policy-update-lists}

Das Arbeiten mit Listen zur Aktualisierung von DRM-Richtlinien umfasst die Verwendung einer `PolicyUpdateListFactory` -Objekt. Wenn Sie eine DRM-Richtlinienaktualisierungsliste erstellen möchten, müssen Sie eine vorhandene DRM-Richtlinienaktualisierungsliste laden und dann überprüfen, ob eine DRM-Richtlinie mithilfe der Java-API aktualisiert oder widerrufen wurde.

So arbeiten Sie mit DRM Policy Update Lists:

1. Richten Sie Ihre Entwicklungsumgebung ein und schließen Sie alle JAR-Dateien ein, die beim Einrichten der Entwicklungsumgebung in einem Projekt enthalten sind.
1. Erstellen Sie eine `ServerCredentialFactory` -Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `PolicyUpdateListFactory` -Instanz mithilfe der `ServerCredential` die Sie erstellt haben.
1. Geben Sie die DRM-Richtlinien-ID an, die Sie widerrufen möchten.
1. Erstellen Sie eine `PolicyRevocationEntry` -Objekt mithilfe der DRM-Richtlinien-ID `String` die Sie soeben erstellt haben, und fügen Sie sie dann der DRM-Liste zur Aktualisierung der Richtlinie hinzu, indem Sie sie an `PolicyUpdateListFactory.addRevocationEntry()`.
1. Generieren Sie die neue DRM-Richtlinienaktualisierungsliste durch Aufruf von `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   Ebenso können Sie DRM-Richtlinien auf die Liste aktualisieren, indem Sie `PolicyUpdateEntry`.
1. Wenn bereits eine DRM-Richtlinienaktualisierungsliste vorhanden ist, können Sie sie für das Laden serialisieren, indem Sie `PolicyUpdateList.getBytes()`.

   Um die Liste zu laden, rufen Sie `PolicyUpdateListFactory.loadPolicyUpdateList()` und übergeben Sie sie in die serialisierte Liste.
1. Stellen Sie sicher, dass die Signatur gültig ist und die Liste vom richtigen Lizenzserver-Zertifikat signiert wurde, indem Sie `PolicyUpdateList.verifySignature()`.
1. DRM-Richtlinien-ID übergeben `String` in `PolicyUpdateList.isRevoked()` , um zu überprüfen, ob ein Eintrag widerrufen wurde.

   Alternativ können Sie die Liste an `HandlerConfiguration` wo sie dann bei der Erteilung von Lizenzen durchgesetzt wird.
Wenn Sie einer vorhandenen Datei weitere Einträge hinzufügen möchten `PolicyUpdateList`müssen Sie eine vorhandene DRM-Richtlinienaktualisierungsliste laden. Daher müssen Sie ein neues DRM erstellen `PolicyUpdateListFactory` -Instanz. Aufruf `PolicyUpdateListFactory.addEntries` , um alle Einträge aus der alten Liste der neuen Liste hinzuzufügen. Aufruf `PolicyUpdateListFactory.addRevocationEntry` oder `addUpdatedEntry` , um neue Sperren oder Aktualisierungseinträge zur DRM PolicyUpdateList hinzuzufügen.

Beispielcode, der zeigt, wie eine DRM-Richtlinienaktualisierungsliste erstellt wird, finden Sie unter `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` im *Befehlszeilenwerkzeuge zur Referenzimplementierung* [!DNL samples] Verzeichnis.
