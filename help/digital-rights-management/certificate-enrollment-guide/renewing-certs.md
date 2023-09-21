---
title: Zertifikate erneuern
description: Zertifikate erneuern
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Zertifikate erneuern{#renew-certificates}

Beachten Sie die folgenden Einschränkungen hinsichtlich der Zertifikatsverlängerung, die auf Ihrer Adobe Primetime DRM SDK-Konfiguration basieren:

* Primetime DRM Production SDK

  Adobe stellt beim Kauf eines Supportvertrags den ersten Satz kostenloser Zertifikate für das Primetime DRM Production SDK bereit. Wenn Sie keinen Support-Vertrag haben, können Sie eine Reihe von Verlängerungszertifikaten erwerben, die für zwei Jahre gültig sind.
* Primetime DRM Evaluation SDK

  Das für dieses SDK festgelegte Zertifikat ist ein Jahr gültig und kann nicht erneuert werden.
* Primetime DRM-Test-SDK

  Das Primetime DRM Trial SDK ist drei Monate lang gültig und Adobe bietet eine Reihe kostenloser Verlängerungszertifikate.

## Implementieren neuer Zertifikate und Verwenden alter Zertifikate für vorhandenen Inhalt {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

In Primetime DRM können Sie einem Lizenzserver gestatten, eine Lizenz für Inhalte auszustellen, die mit vorherigen (oder sogar abgelaufenen) Paketzertifikaten gepackt wurden. Um Ihren Server so zu konfigurieren, dass Lizenzanfragen von zuvor verpackten Inhalten akzeptiert werden, stellen Sie Ihr altes Zertifikat auf Ihrem Server bereit und aktualisieren Sie die Konfigurationsdatei Ihres Servers, damit der Server weiß, wo er die alten Zertifikate finden kann. Weitere Informationen finden Sie unter *Umgang mit Zertifikatsaktualisierungen, wenn von Adobe ausgestellte Zertifikate ablaufen* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

Wenn Ihre Serveranwendung auf der Primetime DRM Reference Implementation basiert, müssen Sie Ihr serverseitiges Programm nicht aktualisieren. Im `flashaccess-refimpl.properties` -Datei, gibt es Felder, in denen Sie zusätzliche Transport- und Lizenzserver-Zertifikate angeben können. Wenn Sie nur ein Zertifikat haben, müssen Sie diese Eigenschaften nicht ausfüllen. Wenn Sie abgelaufene Zertifikate haben und diese Zertifikate verwenden möchten, wenn Sie Lizenzantworten erteilen, müssen Sie diese Zertifikate für die Konfigurationsdatei bereitstellen und den Server neu starten.

Verwenden Sie die folgenden Eigenschaften, um alte Zertifikate anzugeben:

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`
