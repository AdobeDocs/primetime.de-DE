---
seo-title: Zertifikate erneuern
title: Zertifikate erneuern
uuid: 12a560b0-966b-424e-bfe5-22e9c10d8667
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Zertifikate erneuern{#renew-certificates}

Sie sollten die folgenden Einschränkungen hinsichtlich der Zertifikatverlängerung beachten, die auf Ihrer Adobe Primetime DRM SDK-Konfiguration basieren:

* Primetime DRM Production SDK

   Adobe stellt den ersten Satz kostenloser Zertifikate für das Primetime DRM Production SDK bereit, wenn Sie einen Supportvertrag erwerben. Wenn Sie keinen Supportvertrag haben, können Sie eine Reihe von Verlängerungszertifikaten erwerben, die zwei Jahre gültig sind.
* Primetime DRM Evaluation SDK

   Das für dieses SDK festgelegte Zertifikat ist ein Jahr gültig und kann nicht erneuert werden.
* Primetime DRM-Testversion-SDK

   Das Primetime-SDK für die DRM-Testversion ist drei Monate gültig und Adobe stellt einen Satz kostenloser Verlängerungszertifikate bereit.

## Neue Zertifikate implementieren und alte Zertifikate für vorhandenen Inhalt verwenden {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

In Primetime DRM können Sie einem Lizenzserver gestatten, eine Lizenz für Inhalte auszustellen, die mit vorherigen (oder sogar abgelaufenen) Packager-Zertifikaten gepackt wurden. Wenn Sie Ihren Server so konfigurieren möchten, dass Lizenzanforderungen von zuvor verpackten Inhalten akzeptiert werden, stellen Sie Ihr altes Zertifikat für Ihren Server bereit und aktualisieren Sie die Konfigurationsdatei Ihres Servers, damit der Server weiß, wo die alten Zertifikate zu finden sind. Weitere Informationen finden Sie unter *Umgang mit Zertifikatsaktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen* , in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

Wenn Ihre Serveranwendung auf der Primetime-DRM-Referenzimplementierung basiert, müssen Sie Ihr serverseitiges Programm nicht aktualisieren. In der `flashaccess-refimpl.properties` Datei stehen Felder zur Verfügung, in denen Sie zusätzliche Transport- und Lizenzserverzertifikate angeben können. Wenn Sie nur ein Zertifikat haben, müssen Sie diese Eigenschaften nicht ausfüllen. Wenn Sie abgelaufene Zertifikate haben und diese Zertifikate bei der Erteilung von Lizenzantworten verwenden möchten, müssen Sie diese Zertifikate der Konfigurationsdatei bereitstellen und den Server neu starten.

Um alte Zertifikate anzugeben, verwenden Sie die folgenden Eigenschaften:

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

