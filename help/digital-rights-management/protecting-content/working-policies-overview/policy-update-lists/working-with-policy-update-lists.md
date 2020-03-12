---
seo-title: Arbeiten mit Listen zur Aktualisierung der DRM-Richtlinie
title: Arbeiten mit Listen zur Aktualisierung der DRM-Richtlinie
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Listen zur Aktualisierung von DRM-Richtlinien {#drm-policy-update-lists}

Wenn Sie die Verwendungsregeln in einer DRM-Richtlinie nach dem Verpacken von Inhalten aktualisieren, muss der Lizenzserver über die neueste Version verfügen, bevor er Lizenzen ausstellen kann, die eine aktualisierte DRM-Richtlinie verwenden. Eine Möglichkeit, dies zu erreichen, ist eine DRM-Liste zur Aktualisierung der Richtlinie.

Eine DRM-Liste zur Richtlinienaktualisierung wird durch eine Datei dargestellt, die eine Liste der aktualisierten oder gesperrten DRM-Richtlinien enthält. Wenn Sie eine DRM-Richtlinie aktualisieren, müssen Sie eine neue DRM Policy Update-Liste generieren und die Liste regelmäßig auf alle Lizenzserver verschieben.

## Arbeiten mit Listen zur Aktualisierung der DRM-Richtlinie {#working-with-drm-policy-update-lists}

Bei Lizenzservern, die keinen Zugriff auf eine Datenbank zum Speichern von Informationen zu DRM-Richtlinien haben, sollten Sie eine DRM-Liste zur Richtlinienaktualisierung verwenden, um den Lizenzserver über aktualisierte DRM-Richtlinien zu informieren. Die Listen zur Aktualisierung der DRM-Richtlinie können aktualisierte Versionen der DRM-Richtlinien oder eine Liste der DRM-Richtlinien-IDs enthalten, die widerrufen wurden. Wenn eine Liste zur Richtlinienaktualisierung in enthalten ist, `HandlerConfiguration`erzwingt das SDK diese Liste bei der Lizenzerteilung.

Sie können DRM-Richtlinien auch widerrufen, wenn Content-Eigentümer oder -Distributoren die Erteilung von Lizenzen im Rahmen einer bestimmten DRM-Richtlinie einstellen möchten. Eine DRM-Liste zur Richtlinienaktualisierung kann verwendet werden, um DRM-Richtliniensperrungen im SDK zu erzwingen. Sie können auch DRM-Listen zur Richtlinienaktualisierung anwenden, um eine Liste der aktualisierten DRM-Richtlinien für das SDK bereitzustellen.

>[!NOTE]
>
>Wenn Sie eine DRM-Richtlinie widerrufen, werden bereits erteilte Lizenzen nicht automatisch widerrufen. Sie verhindert nur, dass zusätzliche Lizenzen im Rahmen dieser DRM-Politik erteilt werden.

## Listen zur Richtlinienaktualisierung aktualisieren{#update-policy-update-lists}

Das Arbeiten mit DRM-Listen zur Richtlinienaktualisierung umfasst die Verwendung eines `PolicyUpdateListFactory` Objekts. Wenn Sie eine DRM-Liste zur Richtlinienaktualisierung erstellen möchten, müssen Sie eine vorhandene DRM-Policy-Update-Liste laden und dann prüfen, ob eine DRM-Richtlinie mithilfe der Java-API aktualisiert oder widerrufen wurde.

So arbeiten Sie mit Listen zur Aktualisierung der DRM-Richtlinie:

1. Richten Sie Ihre Development-Umgebung ein und fügen Sie alle JAR-Dateien ein, die beim Einrichten der Development-Umgebung in einem Projekt enthalten sind.
1. Erstellen Sie eine `ServerCredentialFactory` Instanz, um die zum Signieren erforderlichen Anmeldeinformationen zu laden.
1. Erstellen Sie eine `PolicyUpdateListFactory` Instanz mit der `ServerCredential` , die Sie erstellt haben.
1. Geben Sie die DRM-Richtlinien-ID an, die Sie widerrufen möchten.
1. Erstellen Sie ein `PolicyRevocationEntry` Objekt mit der soeben erstellten DRM-Richtlinien-ID und fügen Sie es dann der DRM-Liste zur Richtlinienaktualisierung hinzu, indem Sie es an `String` `PolicyUpdateListFactory.addRevocationEntry()`übergeben.
1. Generieren Sie die neue DRM Policy Update Liste durch Aufruf `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   Auf ähnliche Weise können Sie DRM-Richtlinien mit `PolicyUpdateEntry`der Liste aktualisieren.
1. Wenn bereits eine DRM-Liste zur Richtlinienaktualisierung vorhanden ist, können Sie sie beim Laden serialisieren, indem Sie sie aufrufen `PolicyUpdateList.getBytes()`.

   Um die Liste zu laden, rufen Sie sie auf `PolicyUpdateListFactory.loadPolicyUpdateList()` und übergeben Sie sie in der serialisierten Liste.
1. Vergewissern Sie sich, dass die Signatur gültig ist und die Liste durch einen Aufruf vom richtigen Lizenzserverzertifikat signiert wurde `PolicyUpdateList.verifySignature()`.
1. Übergeben Sie die DRM-Richtlinien-ID `String` an, `PolicyUpdateList.isRevoked()` um sicherzustellen, dass ein Eintrag gesperrt wurde.

   Alternativ dazu können Sie die Liste an `HandlerConfiguration` den Ort weiterleiten, an dem sie bei der Erteilung der Lizenzen durchgesetzt wird.
Wenn Sie einer vorhandenen DRM-Liste weitere Einträge hinzufügen möchten, `PolicyUpdateList`müssen Sie eine vorhandene DRM- zur Richtlinienaktualisierung laden. Daher müssen Sie eine neue DRM- `PolicyUpdateListFactory` Instanz erstellen. Aufruf `PolicyUpdateListFactory.addEntries` zum Hinzufügen aller Einträge aus der alten Liste zur neuen Liste. Rufen Sie `PolicyUpdateListFactory.addRevocationEntry` oder `addUpdatedEntry` fügen Sie der DRM PolicyUpdateList alle neuen Sperr- oder Aktualisierungseinträge hinzu.

Beispiel-Code, der das Erstellen einer DRM-Liste zur Richtlinienaktualisierung veranschaulicht, finden Sie `com.adobe.flashaccess.samples.policyupdatelist` im Ordner &quot; `.CreatePolicyUpdateList` Referenz-Implementierungs-Befehlszeilenwerkzeuge *&quot;* [!DNL samples] .
