---
title: Zertifikate erneuern
description: Zertifikate erneuern
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# Zertifikate verlängern{#renew-certificates}

Sie sollten die folgenden Einschränkungen der Zertifikatverlängerung beachten, die auf Ihrer Adobe Primetime DRM SDK-Konfiguration basieren:

* Primetime DRM Production SDK

   Adobe stellt den ersten Satz kostenloser Zertifikate für das Primetime DRM Production SDK bereit, wenn Sie einen Supportvertrag erwerben. Wenn Sie keinen Supportvertrag haben, können Sie eine Reihe von Verlängerungszertifikaten erwerben, die zwei Jahre gültig sind.
* Primetime DRM Evaluation SDK

   Das für dieses SDK festgelegte Zertifikat ist ein Jahr gültig und kann nicht erneuert werden.
* Primetime DRM-Testversion-SDK

   Das Primetime DRM Trial SDK ist drei Monate gültig und die Adobe stellt einen Satz kostenloser Verlängerungszertifikate bereit.

## Implementierung neuer Zertifikate und Verwendung alter Zertifikate für vorhandenen Inhalt {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

In Primetime DRM können Sie einem Lizenzserver gestatten, eine Lizenz für Inhalte auszustellen, die mit vorherigen (oder sogar abgelaufenen) Packager-Zertifikaten gepackt wurden. Wenn Sie Ihren Server so konfigurieren möchten, dass Lizenzanforderungen von zuvor verpackten Inhalten akzeptiert werden, stellen Sie Ihr altes Zertifikat für Ihren Server bereit und aktualisieren Sie die Konfigurationsdatei Ihres Servers, damit der Server weiß, wo die alten Zertifikate zu finden sind. Weitere Informationen finden Sie unter *Verarbeiten von Zertifikataktualisierungen, wenn von der Adobe ausgestellte Zertifikate ablaufen* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

Wenn Ihre Serveranwendung auf der Primetime-DRM-Referenzimplementierung basiert, müssen Sie Ihr serverseitiges Programm nicht aktualisieren. In der Datei `flashaccess-refimpl.properties` gibt es Felder, in denen Sie zusätzliche Transport- und Lizenzserverzertifikate angeben können. Wenn Sie nur ein Zertifikat haben, müssen Sie diese Eigenschaften nicht ausfüllen. Wenn Sie abgelaufene Zertifikate haben und diese Zertifikate verwenden möchten, wenn Sie Lizenzantworten ausstellen, müssen Sie diese Zertifikate der Konfigurationsdatei bereitstellen und den Server neu starten.

Um alte Zertifikate anzugeben, verwenden Sie die folgenden Eigenschaften:

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

