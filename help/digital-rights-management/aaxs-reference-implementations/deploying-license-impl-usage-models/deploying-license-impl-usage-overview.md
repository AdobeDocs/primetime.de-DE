---
seo-title: Implementieren der Übersicht über die Nutzungsmodelle
title: Implementieren der Übersicht über die Nutzungsmodelle
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Implementieren der Übersicht über die Nutzungsmodelle {#implementing-the-usage-models-overview}

Die Referenzimplementierung enthält eine Geschäftslogik, mit der gezeigt wird, wie die folgenden vier verschiedenen Nutzungsmodelle für ein Paket von Inhalten aktiviert werden können:

* Download-to-own (DTO)
* Miete/Video-on-Demand (VOD)
* Abonnement (alles, was Sie essen können)
* Werbefinanziert

Um die Demo des Gebrauchsmodells zu aktivieren, geben Sie die benutzerdefinierte Eigenschaft `RI_UsageModelDemo=true` zur Verpackungszeit an. Wenn Sie Inhalte mit dem Befehlszeilenwerkzeug von Media Packager verpacken, geben Sie Folgendes an:

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Wenn Sie den optionalen Demo-Modus nicht zur Verpackungszeit aktivieren, verwendet der Lizenzserver die beim Verpacken angegebene Richtlinie, um eine Lizenz auszustellen. Wenn mehrere Richtlinien angegeben wurden, verwendet der Lizenzserver die erste gültige Richtlinie.

In der Demo steuert die Geschäftslogik auf dem Server die tatsächlichen Attribute der generierten Lizenzen. Beim Verpacken müssen nur minimale Richtlinieninformationen in den Inhalt aufgenommen werden. Insbesondere muss die Richtlinie nur angeben, ob für den Zugriff auf den Inhalt eine Authentifizierung erforderlich ist. Um alle vier Nutzungsmodelle zu aktivieren, fügen Sie eine Richtlinie hinzu, die den anonymen Zugriff zulässt (für das Ad-funding-Modell), und eine Richtlinie, die die Authentifizierung von Benutzername und Kennwort erfordert (für die anderen 3 Verwendungsmodelle). Beim Anfordern einer Lizenz kann eine Clientanwendung anhand der Authentifizierungsinformationen in den Richtlinien bestimmen, ob der Benutzer zur Authentifizierung aufgefordert werden soll.

Um das Nutzungsmodell zu steuern, unter dem ein bestimmter Benutzer eine Lizenz erhalten soll, können der Referenz-Implementierungsdatenbank Einträge hinzugefügt werden. Die `Customer` Tabelle enthält Benutzernamen und Kennwörter für die Authentifizierung von Benutzern. Es gibt auch an, ob der Benutzer über ein Abonnement verfügt. Anwendern mit Abonnements werden Lizenzen nach dem *Abonnement* -Nutzungsmodell erteilt. Um einem Benutzer Zugriff auf die Nutzungsmodelle *Download zu eigenen* oder *Video-on-Demand* `CustomerAuthorization` zu gewähren, kann der Tabelle ein Eintrag hinzugefügt werden, in dem alle Inhalte angegeben werden, auf die der Benutzer zugreifen darf, sowie das Nutzungsmodell. Einzelheiten zum Ausfüllen der einzelnen Tabellen finden Sie im [!DNL PopulateSampleDB.sql] Skript.

Wenn ein Benutzer eine Lizenz anfordert, prüft der Referenz-Implementierungsserver die vom Client gesendeten Metadaten, um festzustellen, ob der Inhalt mit der `RI_UsageModelDemo` Eigenschaft gepackt wurde. In diesem Fall werden die folgenden Geschäftsregeln verwendet:

* Wenn eine der Richtlinien Authentifizierung erfordert:

   * Wenn die Anforderung ein gültiges Authentifizierungstoken enthält, suchen Sie in der Tabelle &quot;Kundendatenbank&quot;nach dem Benutzer. Wenn der Benutzer gefunden wurde:

      * Wenn die `Customer.IsSubscriber` Eigenschaft aktiviert ist `true`, generieren Sie eine Lizenz für das *Abonnement* -Nutzungsmodell und senden Sie es an den Benutzer.

      * Suchen Sie in der `CustomerAuthorization` Datenbanktabelle nach einem Eintrag für diese Benutzer- und Inhalts-ID. Wenn ein Datensatz gefunden wurde:

         * Falls `CustomerAuthorization.UsageType` dies `DTO`der Fall ist, erstellen Sie eine Lizenz für das *Nutzungsmodell &quot;In Eigene* herunterladen&quot;und senden Sie es an den Benutzer.

         * Falls `CustomerAuthorization.UsageType` dies `VOD`der Fall ist, erstellen Sie eine Lizenz für das *Video On Demand* -Nutzungsmodell und senden Sie es an den Benutzer.
   * Wenn keine der Richtlinien den anonymen Zugriff zulässt:

      * Wenn die Anforderung kein gültiges Authentifizierungstoken enthält, geben Sie den Fehler &quot;Authentifizierung erforderlich&quot;zurück.
      * Andernfalls wird der Fehler &quot;nicht autorisiert&quot;zurückgegeben.


* Wenn eine der Richtlinien den anonymen Zugriff zulässt, generieren Sie eine Lizenz für das Ad-finanziert-Nutzungsmodell und senden Sie sie an den Benutzer.

Bevor der Referenz-Implementierungsserver Lizenzen für die Demo zum Verwendungsmodell ausstellen kann, muss der Server so konfiguriert werden, dass angegeben wird, wie Lizenzen für jedes der vier Nutzungsmodelle generiert werden. Dies erfolgt durch Angabe einer Richtlinie für jedes Nutzungsmodell. Die Referenzimplementierung umfasst vier Beispielrichtlinien ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) oder Sie können Ihre eigenen Richtlinien ersetzen. Legen Sie [!DNL flashaccess-refimpl.properties]die folgenden Eigenschaften fest, um die für jedes Nutzungsmodell zu verwendende Richtlinie anzugeben und die Richtliniendateien in dem von der `config.resourcesDirectory` Eigenschaft angegebenen Ordner abzulegen:

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

