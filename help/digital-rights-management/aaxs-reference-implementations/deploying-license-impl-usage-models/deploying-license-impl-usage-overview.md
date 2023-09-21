---
title: Übersicht über das Implementieren von Nutzungsmodellen
description: Übersicht über das Implementieren von Nutzungsmodellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Übersicht über das Implementieren von Nutzungsmodellen {#implementing-the-usage-models-overview}

Die Referenzimplementierung umfasst eine Geschäftslogik, die zeigt, wie die folgenden vier verschiedenen Nutzungsmodelle für ein gepacktes Inhaltselement aktiviert werden:

* Download-to-own (DTO)
* Vermietung/Video-on-Demand (VOD)
* Anmeldung (alles, was Sie essen können)
* Anzeigenfinanziert

Um die Demo des Nutzungsmodells zu aktivieren, geben Sie die benutzerdefinierte Eigenschaft an `RI_UsageModelDemo=true` zum Zeitpunkt der Verpackung. Wenn Sie Inhalte mit dem Befehlszeilen-Tool Media Packager verpacken, geben Sie Folgendes an:

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>Wenn Sie den optionalen Demomodus nicht während der Verpackung aktivieren, verwendet der Lizenzserver die bei der Verpackung angegebene Richtlinie, um eine Lizenz zu erteilen. Wenn mehrere Richtlinien angegeben wurden, verwendet der Lizenzserver die erste gültige Richtlinie.

In der Demo steuert die Geschäftslogik auf dem Server die tatsächlichen Attribute der generierten Lizenzen. Zum Zeitpunkt der Verpackung dürfen nur minimale Richtlinieninformationen in den Inhalt aufgenommen werden. Insbesondere muss die Richtlinie nur angeben, ob für den Zugriff auf den Inhalt eine Authentifizierung erforderlich ist. Um alle vier Nutzungsmodelle zu aktivieren, fügen Sie eine Richtlinie hinzu, die den anonymen Zugriff ermöglicht (für das Modell mit Anzeigenunterstützung), und eine Richtlinie, für die die Authentifizierung von Benutzernamen und Kennwort erforderlich ist (für die anderen 3 Nutzungsmodelle). Beim Anfordern einer Lizenz kann eine Client-Anwendung anhand der Authentifizierungsinformationen in den Richtlinien bestimmen, ob der Benutzer zur Authentifizierung aufgefordert werden soll.

Um das Nutzungsmodell zu steuern, unter dem ein bestimmter Benutzer eine Lizenz erhalten soll, können Einträge zur Referenz-Implementierungsdatenbank hinzugefügt werden. Die `Customer` -Tabelle enthält Benutzernamen und Kennwörter für die Authentifizierung von Benutzern. Sie gibt auch an, ob der Benutzer über ein Abonnement verfügt. Benutzer mit Abonnements erhalten Lizenzen im Rahmen der *Abonnement* Nutzungsmodell. So gewähren Sie einem Benutzer Zugriff unter *Herunterladen in Eigene* oder *Video on Demand* Verwendungsmodelle verwenden, kann ein Eintrag zum `CustomerAuthorization` -Tabelle, die jedes Inhaltselement angibt, auf das der Benutzer zugreifen darf, und das Nutzungsmodell. Siehe [!DNL PopulateSampleDB.sql] -Skript für Details zum Ausfüllen der einzelnen Tabellen.

Wenn ein Benutzer eine Lizenz anfordert, überprüft der Referenz-Implementierungsserver die vom Client gesendeten Metadaten, um festzustellen, ob der Inhalt mit dem `RI_UsageModelDemo` -Eigenschaft. Wenn ja, werden die folgenden Geschäftsregeln verwendet:

* Wenn eine der Richtlinien Authentifizierung erfordert:

   * Wenn die Anfrage ein gültiges Authentifizierungstoken enthält, suchen Sie in der Tabelle der Kundendatenbank nach dem Benutzer. Wenn der Benutzer gefunden wurde:

      * Wenn die Variable `Customer.IsSubscriber` Eigenschaft ist `true`, generieren Sie eine Lizenz für die *Abonnement* Nutzungsmodell verwenden und an den Benutzer senden.

      * Suchen Sie nach einem Datensatz im `CustomerAuthorization` Datenbanktabelle für diese Benutzer- und Inhalts-ID. Wenn ein Datensatz gefunden wurde:

         * Wenn `CustomerAuthorization.UsageType` is `DTO`, generieren Sie eine Lizenz für die *Herunterladen in Eigene* Nutzungsmodell verwenden und an den Benutzer senden.

         * Wenn `CustomerAuthorization.UsageType` is `VOD`, generieren Sie eine Lizenz für die *Video On Demand* Nutzungsmodell verwenden und an den Benutzer senden.

   * Wenn keine der Richtlinien den anonymen Zugriff zulässt:

      * Wenn die Anfrage kein gültiges Authentifizierungstoken enthält, geben Sie den Fehler &quot;Authentifizierung erforderlich&quot;zurück.
      * Andernfalls wird der Fehler &quot;Nicht autorisiert&quot;zurückgegeben.

* Wenn eine der Richtlinien den anonymen Zugriff zulässt, generieren Sie eine Lizenz für das Ad-supported-Nutzungsmodell und senden Sie sie an den Benutzer.

Bevor der Referenz-Implementierungsserver Lizenzen für die Demo des Nutzungsmodells ausgeben kann, muss der Server so konfiguriert werden, dass er angibt, wie Lizenzen für jedes der vier Nutzungsmodelle generiert werden. Dies geschieht durch Angabe einer Richtlinie für jedes Nutzungsmodell. Die Referenzimplementierung umfasst vier Beispielrichtlinien ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) oder Sie können Ihre eigenen Richtlinien ersetzen. In [!DNL flashaccess-refimpl.properties], legen Sie die folgenden Eigenschaften fest, um die Richtlinie anzugeben, die für jedes Nutzungsmodell verwendet werden soll, und platzieren Sie die Richtliniendateien in dem Ordner, der durch das `config.resourcesDirectory` Eigenschaft:

```
# Policy file name for Download To Own usage  
RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol  
# Policy file name for Rental usage  
RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol  
# Policy file name for Subscription usage  
RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol  
# Policy file name for Ad Supported (free) usage  
RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
```
