---
title: Geschäftsregeln der Demovorlage für Nutzungsmodelle
description: Geschäftsregeln der Demovorlage für Nutzungsmodelle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Geschäftsregeln der Demovorlage für Nutzungsmodelle{#usage-model-demo-business-rules}

Wenn ein Benutzer eine Lizenz anfordert, überprüft der Referenz-Implementierungsserver die vom Client gesendeten Metadaten, um festzustellen, ob der Inhalt mithilfe der `RI_UsageModelDemo` -Eigenschaft. Ist dies der Fall, wendet der Server die folgenden Geschäftsregeln an.

* Wenn eine der DRM-Richtlinien Authentifizierung erfordert:

   * Wenn die Anfrage ein gültiges Authentifizierungstoken enthält, suchen Sie in der Tabelle der Kundendatenbank nach dem Namen des Benutzers.

     Wenn Sie den Namen des Benutzers nicht finden können, führen Sie die folgenden Aufgaben aus:

      * Wenn die Variable `Customer.IsSubscriber` -Eigenschaft auf `true`, müssen Sie eine Lizenz für die *`Subscription`* Nutzungsmodell verwenden und an den Benutzer senden.

      * Suchen Sie nach einem Datensatz im `CustomerAuthorization` Datenbanktabelle für den Namen des Benutzers und die Inhalts-ID.

     Wenn Sie den Benutzerdatensatz finden können, führen Sie die folgenden Aufgaben aus:

      * Wenn die Variable `CustomerAuthorization.UsageType` -Eigenschaft auf `DTO`generieren Sie eine Lizenz für das DTO-Nutzungsmodell und senden Sie es an den Benutzer.

      * Wenn die Variable `CustomerAuthorization.UsageType` -Eigenschaft auf `VOD`, generieren Sie eine Lizenz für das VOD-Nutzungsmodell und senden Sie es an den Benutzer.

     Wenn keine der DRM-Richtlinien den anonymen Zugriff zulässt, führen Sie die folgenden Aufgaben aus:

      * Wenn die Anfrage kein gültiges Authentifizierungstoken enthält, müssen Sie den Fehler &quot;Authentifizierung erforderlich&quot;zurückgeben.
      * Andernfalls wird der Fehler &quot;Nicht autorisiert&quot;zurückgegeben.

* Wenn eine der DRM-Richtlinien den anonymen Zugriff zulässt, generieren Sie eine Lizenz für das Ad-finanzierte Nutzungsmodell und senden Sie sie an den Benutzer.
