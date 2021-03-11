---
title: Arbeiten mit Listen zur Aktualisierung der DRM-Richtlinie
description: Arbeiten mit Listen zur Aktualisierung der DRM-Richtlinie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# DRM-Richtlinien aktualisieren Listen {#drm-policy-update-lists}

Wenn Sie die Verwendungsregeln in einer DRM-Richtlinie nach dem Verpacken von Inhalten aktualisieren, muss der Lizenzserver über die neueste Version verfügen, bevor er Lizenzen ausstellen kann, die eine aktualisierte DRM-Richtlinie verwenden. Eine Möglichkeit, dies zu erreichen, ist eine DRM-Liste zur Aktualisierung der Richtlinie.

Eine DRM-Liste zur Richtlinienaktualisierung wird durch eine Datei dargestellt, die eine Liste der aktualisierten oder gesperrten DRM-Richtlinien enthält. Wenn Sie eine DRM-Richtlinie aktualisieren, müssen Sie eine neue DRM Policy Update-Liste generieren und die Liste regelmäßig auf alle Lizenzserver verschieben.

## Arbeiten mit DRM Policy Update-Listen {#working-with-drm-policy-update-lists}

Bei Lizenzservern, die keinen Zugriff auf eine Datenbank zum Speichern von Informationen zu DRM-Richtlinien haben, sollten Sie eine DRM-Liste zur Richtlinienaktualisierung verwenden, um den Lizenzserver über aktualisierte DRM-Richtlinien zu informieren. Die Listen zur Aktualisierung der DRM-Richtlinie können aktualisierte Versionen der DRM-Richtlinien oder eine Liste der DRM-Richtlinien-IDs enthalten, die widerrufen wurden. Wenn eine Liste für Richtlinienaktualisierungen in `HandlerConfiguration` enthalten ist, erzwingt das SDK diese Liste bei der Lizenzerteilung.

Sie können DRM-Richtlinien auch widerrufen, wenn Content-Eigentümer oder -Distributoren die Erteilung von Lizenzen im Rahmen einer bestimmten DRM-Richtlinie einstellen möchten. Eine DRM-Liste zur Richtlinienaktualisierung kann verwendet werden, um DRM-Richtliniensperrungen im SDK zu erzwingen. Sie können auch DRM-Listen zur Richtlinienaktualisierung anwenden, um eine Liste der aktualisierten DRM-Richtlinien für das SDK bereitzustellen.

>[!NOTE]
>
>Wenn Sie eine DRM-Richtlinie widerrufen, werden bereits erteilte Lizenzen nicht automatisch widerrufen. Sie verhindert nur, dass zusätzliche Lizenzen im Rahmen dieser DRM-Politik erteilt werden.

## Listen zur Aktualisierung von Richtlinien{#update-policy-update-lists} aktualisieren

Das Arbeiten mit DRM-Listen zur Richtlinienaktualisierung umfasst die Verwendung eines `PolicyUpdateListFactory`-Objekts. Wenn Sie eine DRM-Liste zur Richtlinienaktualisierung erstellen möchten, müssen Sie eine vorhandene DRM-Policy-Update-Liste laden und dann prüfen, ob eine DRM-Richtlinie mithilfe der Java-API aktualisiert oder widerrufen wurde.

So arbeiten Sie mit Listen zur Aktualisierung der DRM-Richtlinie:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die beim Einrichten der Development-Umgebung in einem Projekt enthalten sind.
1. Erstellen Sie eine `ServerCredentialFactory`-Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `PolicyUpdateListFactory`-Instanz mit dem erstellten `ServerCredential`.
1. Geben Sie die DRM-Richtlinien-ID an, die Sie widerrufen möchten.
1. Erstellen Sie ein `PolicyRevocationEntry`-Objekt mit der soeben erstellten DRM-Richtlinien-ID `String` und fügen Sie es dann der DRM-Liste zur Richtlinienaktualisierung hinzu, indem Sie es an `PolicyUpdateListFactory.addRevocationEntry()` übergeben.
1. Generieren Sie die neue DRM Policy Update Liste, indem Sie `PolicyUpdateListFactory.generatePolicyUpdateList()` aufrufen.

   Ebenso können Sie DRM-Richtlinien mit `PolicyUpdateEntry` auf die Liste aktualisieren.
1. Wenn bereits eine DRM-Liste zur Richtlinienaktualisierung vorhanden ist, können Sie diese für das Laden serialisieren, indem Sie `PolicyUpdateList.getBytes()` aufrufen.

   Rufen Sie zum Laden der Liste `PolicyUpdateListFactory.loadPolicyUpdateList()` auf und übergeben Sie sie in der serialisierten Liste.
1. Vergewissern Sie sich, dass die Signatur gültig ist und die Liste mit dem richtigen Lizenzserverzertifikat signiert wurde, indem Sie `PolicyUpdateList.verifySignature()` aufrufen.
1. Übergeben Sie die DRM-Richtlinien-ID `String` an `PolicyUpdateList.isRevoked()`, um sicherzustellen, dass ein Eintrag gesperrt wurde.

   Alternativ können Sie die Liste an `HandlerConfiguration` weitergeben, wo sie dann immer dann erzwungen wird, wenn Lizenzen erteilt werden.
Wenn Sie einer vorhandenen `PolicyUpdateList` weitere Einträge hinzufügen möchten, müssen Sie eine vorhandene DRM-Liste zur Richtlinienaktualisierung laden. Daher müssen Sie eine neue DRM `PolicyUpdateListFactory`-Instanz erstellen. Rufen Sie `PolicyUpdateListFactory.addEntries` auf, um der neuen Liste alle Einträge aus der alten Liste hinzuzufügen. Rufen Sie `PolicyUpdateListFactory.addRevocationEntry` oder `addUpdatedEntry` auf, um der DRM PolicyUpdateList neue Sperrungs- oder Aktualisierungseinträge hinzuzufügen.

Beispielcode, der das Erstellen einer DRM-Liste zur Richtlinienaktualisierung veranschaulicht, finden Sie unter `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` im Ordner *Referenzimplementierungs-Befehlszeilenwerkzeuge* [!DNL samples].
