---
description: 'null'
seo-description: 'null'
seo-title: Demogeschäftsregeln zum Gebrauchsmodell
title: Demogeschäftsregeln zum Gebrauchsmodell
uuid: c55f85be-5ecb-4a78-b47d-7001ec207d3a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Demogeschäftsregeln für das Gebrauchsmodell{#usage-model-demo-business-rules}

Wenn ein Benutzer eine Lizenz anfordert, prüft der Referenz-Implementierungsserver die vom Client gesendeten Metadaten, um zu ermitteln, ob der Inhalt mithilfe der `RI_UsageModelDemo`-Eigenschaft gepackt wurde. In diesem Fall wendet der Server die folgenden Geschäftsregeln an.

* Wenn eine der DRM-Richtlinien eine Authentifizierung erfordert:

   * Wenn die Anforderung ein gültiges Authentifizierungstoken enthält, suchen Sie in der Tabelle für die Kundendatenbank nach dem Namen des Benutzers.

      Wenn Sie den Benutzernamen nicht finden können, führen Sie die folgenden Aufgaben aus:

      * Wenn die `Customer.IsSubscriber`-Eigenschaft auf `true` eingestellt ist, müssen Sie eine Lizenz für das *`Subscription`*-Nutzungsmodell generieren und es an den Benutzer senden.

      * Suchen Sie in der Datenbanktabelle `CustomerAuthorization` nach einem Datensatz für den Namen des Benutzers und die Inhalts-ID.

      Wenn Sie den Benutzerdatensatz finden können, führen Sie die folgenden Aufgaben aus:

      * Wenn die `CustomerAuthorization.UsageType`-Eigenschaft auf `DTO` eingestellt ist, generieren Sie eine Lizenz für das DTO-Nutzungsmodell und senden Sie sie an den Benutzer.

      * Wenn die `CustomerAuthorization.UsageType`-Eigenschaft auf `VOD` eingestellt ist, generieren Sie eine Lizenz für das VOD-Nutzungsmodell und senden Sie es an den Benutzer.

      Wenn keine der DRM-Richtlinien den anonymen Zugriff zulässt, führen Sie die folgenden Aufgaben aus:

      * Wenn die Anforderung kein gültiges Authentifizierungstoken enthält, müssen Sie den Fehler &quot;Authentifizierung erforderlich&quot;zurückgeben.
      * Andernfalls wird der Fehler &quot;nicht autorisiert&quot;zurückgegeben.



* Wenn eine der DRM-Richtlinien den anonymen Zugriff zulässt, generieren Sie eine Lizenz für das Ad-finanziert-Nutzungsmodell und senden Sie es an den Benutzer.

