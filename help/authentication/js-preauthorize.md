---
title: Vorautorisieren
description: JavaScript-Vorabautorisierung
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 0%

---


# Vorautorisieren {#js-preauthorize}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Übersicht {#preauth-overview}

Die API-Methode Preauthorize (Vorabautorisierung) wird von Anwendungen verwendet, um Entscheidungen über die Vorabautorisierung für eine oder mehrere Ressourcen zu erhalten. Die API-Anfrage zur Vorabautorisierung sollte für UI-Hinweise und/oder Inhaltsfilterung verwendet werden. Vor dem Gewähren des Benutzerzugriffs auf die angegebenen Ressourcen muss eine tatsächliche Autorisierungs-API-Anfrage gestellt werden.

Wenn ein unerwarteter Fehler (z. B. ein Netzwerkproblem und ein nicht verfügbarer MVPD-Autorisierungsendpunkt) auftritt, wenn eine API-Anfrage zur Vorabautorisierung von den Adobe Primetime-Authentifizierungsdiensten verarbeitet wird, werden eine oder mehrere separate Fehlerinformationen für die betroffenen Ressourcen als Teil des Antwortergebnisses zur Vorabautorisierung der API eingefügt.

### public preauthorize(request: PreauthorizeRequest, callback: AccessEnablerCallback&lt;any>): void {#preauth-method}

**Beschreibung:** Diese Methode wird von Anwendungen verwendet, um die (informativen) Entscheidungen authentifizierter Benutzer vom Adobe Primetime-Authentifizierungsdienst zur Anzeige bestimmter geschützter Ressourcen zu erhalten. Dies dient hauptsächlich dazu, die Benutzeroberfläche der Anwendung zu dekorieren (z. B. um den Zugriffsstatus mit Symbolen zum Sperren und Entsperren anzugeben).

**Verfügbarkeit:** v4.4.0+

**Parameter:**

* `PreauthorizeRequest`: Builder-Objekt, das zum Definieren der Anforderung verwendet wird
* `AccessEnablerCallback`: Callback, der zum Zurückgeben der API-Antwort verwendet wird
* `PreauthorizeResponse`: Objekt, das zum Zurückgeben des API-Antwortinhalts verwendet wird

### class PreauthorizeRequestBuilder {#preath-req-builder-class}

#### setResources(resources: Zeichenfolge[]): PreauthorizeRequestBuilder {#set-res-preath-req-buildr}

* Legt die Liste der Ressourcen fest, für die Sie Vorabentscheidungen zur Autorisierung abrufen möchten.
* Es ist obligatorisch, sie für die Verwendung der Vorabautorisierungs-API festzulegen.
* Jedes Element in der Liste muss ein String sein, der entweder den Ressourcen-ID-Wert oder das Medien-RSS-Fragment darstellt, das mit dem MVPD abgestimmt werden muss.
* Diese Methode legt die Informationen nur im Kontext des aktuellen `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger dieses Methodenaufrufs darstellt.

* So erstellen Sie einen tatsächlichen `PreauthorizeRequest` Sie können einen Blick auf `PreauthorizeRequestBuilder`s -Methode:

```JavaScript
  build(): PreauthorizeRequest
```

* `@param {string[]}` Ressourcen. Die Liste der Ressourcen, für die Sie Entscheidungen zur Vorabautorisierung erhalten möchten.
* `@returns {PreauthorizeRequestBuilder}` Der Verweis auf dasselbe `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger des Methodenaufrufs darstellt.
* Dadurch wird die Erstellung von Methodenverketten ermöglicht.

#### disableFeatures(...Funktionen: Zeichenfolge[]): PreauthorizeRequestBuilder {#disabl-featres-preauth-req-buildr}

* Legt die Funktionen fest, die deaktiviert werden sollen, wenn Sie Entscheidungen über die Vorabautorisierung treffen.
* Diese Funktion legt die Informationen nur im Kontext des aktuellen `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger dieses Funktionsaufrufs darstellt.
* So erstellen Sie einen tatsächlichen `PreauthorizeRequest` Sie können einen Blick auf `PreauthorizeRequestBuilder`Funktion &quot;s&quot;:

```JavaScript
public func build() -> PreauthorizeRequest
```

* `@param {string[]}` Funktionen. Die Funktionen, die deaktiviert werden sollen.
* `@returns` Der Verweis auf dasselbe `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger des Funktionsaufrufs darstellt.
* Dies geschieht, um die Erstellung von Funktionsketten zu ermöglichen.

#### build(): PreauthorizeRequest {#preauth-req}

* Erstellt und ruft die Referenz eines neuen `PreauthorizeRequest` -Objektinstanz.
* Diese Methode instanziiert eine neue `PreauthorizeRequest` -Objekt jedes Mal, wenn es aufgerufen wird.
* Diese Methode verwendet die im Voraus im Kontext des aktuellen `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger dieses Methodenaufrufs darstellt.
* Beachten Sie, dass diese Methode keine Nebenwirkungen hervorruft;
* Daher ändert es den Status des SDK oder den Status des `PreauthorizeRequestBuilder` -Objektinstanz, die den Empfänger dieses Methodenaufrufs darstellt.
* Das bedeutet, dass aufeinander folgende Aufrufe dieser Methode für denselben Empfänger unterschiedliche neue `PreauthorizeRequest` -Objektinstanzen mit denselben Informationen, sofern die Werte auf die `PreauthorizeRequestBuilder` wobei zwischen den Aufrufen nicht geändert wurde.
* Falls Sie keine der bereitgestellten Informationen (Ressourcen und Zwischenspeicherung) aktualisieren müssen, können Sie die PreauthorizeRequest -Instanz für mehrere Verwendungen der Vorabautorisierungs-API wiederverwenden.
* `@returns {PreauthorizeRequest}`

### interface AccessEnablerCallback&lt;t> {#interface-access-enablr-callback}

#### onResponse(result: T); {#on-response-result}

* Rückruf der Antwort, der vom SDK aufgerufen wurde, wenn die API-Anfrage zur Vorabautorisierung erfüllt wurde.
* Das Ergebnis ist entweder ein erfolgreiches Ergebnis oder ein Fehlerergebnis mit einem Status.
* `@param {T} result`

#### onFailure(result: T); {#on-failure-result}

* Fehler-Callback, der vom SDK aufgerufen wird, wenn die API-Anfrage zur Vorabautorisierung nicht gewartet werden konnte.
* Das Ergebnis ist ein Fehlerergebnis mit einem Status.
* `@param {T} result`

### class PreauthorizeResponse {#preauth-response-class}

#### öffentlicher Status: Status; {#public-status}

* Gibt Folgendes zurück: Zusätzliche Statusinformationen (Status) im Fall eines Fehlschlagens.
* Kann eine `null` -Wert.

#### öffentliche Entscheidungen: Entscheidung[]; {#public-decisions}

* Gibt Folgendes zurück: Liste der Entscheidungen über die Vorabgenehmigung. Eine Entscheidung für jede Ressource.
* Die Liste kann im Falle eines Fehlers leer sein.

### Klassenstatus {#class-status}

#### öffentlicher Status: Nummer; {#public-status-numbr}

* Der HTTP-Antwortstatus-Code, wie in RFC 7231 dokumentiert.
* Kann 0 sein, falls `Status` stammt aus dem SDK anstelle von Adobe Primetime Authentication Services.

#### öffentlicher Code: Nummer; {#public-code-numbr}

* Der standardmäßige Fehlercode für Adobe Primetime Authentication Services.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.

#### öffentliche Nachricht: Zeichenfolge; {#public-msg-string}

* Die detaillierte Meldung, die in einigen Fällen von den MVPD-Autorisierungsendpunkten oder von Regeln zur Programmabbauung bereitgestellt wird.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.

#### öffentliche Details: Zeichenfolge; {#public-details-strng}

* Enthält eine detaillierte Meldung, die in einigen Fällen von den MVPD-Autorisierungsendpunkten oder von Regeln zur Programmabbaubarkeit bereitgestellt wird.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.


#### public helpUrl: Zeichenfolge; {#public-help-url-string}

* Die URL, die auf weitere Informationen zum Auftreten dieses Status/Fehlers und zu möglichen Lösungen verweist.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.

#### public trace: Zeichenfolge; {#public-trace-string}

* Die eindeutige Kennung für diese Antwort, die verwendet werden kann, wenn der Support kontaktiert wird, um bestimmte Probleme in komplexeren Szenarien zu identifizieren.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.

#### öffentliche Maßnahmen: Zeichenfolge; {#public-action-string}

* Die empfohlene Maßnahme zur Behebung der Situation.
   * **Keine**: Leider gibt es keine vordefinierten Maßnahmen, um dieses Problem zu beheben. Dies könnte auf einen falschen Aufruf der öffentlichen API hindeuten
   * **Konfiguration**: Eine Konfigurationsänderung ist über das TVE-Dashboard oder durch Kontaktaufnahme mit dem Support erforderlich.
   * **application-registration**: Die Anmeldung muss sich selbst registrieren.
   * **Authentifizierung**: Der Benutzer muss sich authentifizieren oder erneut authentifizieren.
   * **Autorisierung**: Der Benutzer muss die Autorisierung für die jeweilige Ressource einholen.
   * **Abbau**: Eine gewisse Abbauweise sollte angewendet werden.
   * **Wiederholen**: Das Problem kann durch Wiederholen der Anfrage gelöst werden
   * **retry-after**: Wenn Sie die Anfrage nach dem angegebenen Zeitraum erneut ausführen, kann das Problem möglicherweise behoben sein.
* Kann eine leere Zeichenfolge oder eine `null` -Wert.

### Klasse {#class-decision}

#### öffentliche ID: Zeichenfolge; {#public-id-string}

* Die Ressourcen-ID, für die die Entscheidung abgerufen wurde.

#### öffentlich zugelassen: boolesch; {#public-auth-boolean}

* Der -Wert der Markierung, der angibt, ob die Entscheidung erfolgreich war oder nicht.

#### öffentlicher Fehler: Status; {#public-error-status}

* Zusätzliche Statusinformationen für den Fall, dass ein Fehler aufgetreten ist. Kann eine `null` -Wert.

## Beispiel für Client-Implementierung {#client-imp-example}

```JavaScript
let accessEnablerApi = new window.AccessEnabler.AccessEnabler("software statement");
let accessEnablerModels = window.AccessEnabler.models;



// Build request
let requestBuilder = new accessEnablerModels.PreauthorizeRequest.getBuilder();
let request = requestBuilder
    .setResources(["RES01", "RES02", "RES03"])
    .disableFeatures("LOCAL_CACHE")
    .build();



// Create callback
let callback = {
    onResponse(response) {
        // Handle onResponse
    },
    onFailure(response) {
        // Handle onFailure
    }
};

// Invoke call
accessEnablerApi.preauthorize(request, callback);
```


## Szenario-Beispiele {#scenario-examples}

### Szenario 1: Alle beantragten Ressourcen wurden genehmigt {#all-req-res-auth}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Behinderte</td>
    <td>

```JavaScript
        {
    "decisions": [
        {
        "id": "RES01",
        "authorized": true
        },
        {
        "id": "RES02",
        "authorized": true
        },
        {
        "id": "RES03",
        "authorized": true
        }
    ]
    }    
```

</td>
  </tr>
</tbody>


### Szenario 2: Einige der angeforderten Ressourcen wurden autorisiert. {#sm-req-res-auth}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Behinderte</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;Beschlüsse&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;autorisiert&quot;: true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;autorisiert&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;autorisiert&quot;: true
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;Beschlüsse&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;autorisiert&quot;: true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Der MVPD hat eine \&quot;Ablehnen\&quot;-Entscheidung zurückgegeben, wenn er eine Vorabautorisierung für die angegebene Ressource anfordert.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;autorisiert&quot;: true
    },
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Szenario 3: Keine der beantragten Ressourcen wurde genehmigt. {#none-req-res-auth}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Behinderte</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;Beschlüsse&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;autorisiert&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;autorisiert&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;autorisiert&quot;: false
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Aktiviert</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;Beschlüsse&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Der MVPD hat eine \&quot;Ablehnen\&quot;-Entscheidung zurückgegeben, wenn er eine Vorabautorisierung für die angegebene Ressource anfordert.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Der MVPD hat eine \&quot;Ablehnen\&quot;-Entscheidung zurückgegeben, wenn er eine Vorabautorisierung für die angegebene Ressource anfordert.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;maximum_execution_time_exceeded&quot;,
    &quot;message&quot;: &quot;Die Anfrage wurde in der maximal zulässigen Zeit nicht abgeschlossen. Ein erneuter Versuch mit der Anfrage kann das Problem lösen.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;retry&quot;
    }
    }
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Szenario 4: Ungültige Clientanfrage - keine Ressourcen angegeben. {#bad-cl-req-no-res-sp}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Deaktiviert/Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 400,
    &quot;code&quot;: &quot;internal_error&quot;,
    &quot;message&quot;: &quot;Die Anfrage ist aufgrund eines internen Fehlers fehlgeschlagen.&quot;
    &quot;details&quot;: &quot;Erforderlicher String[]-Parameter &#39;resource&#39; ist nicht vorhanden&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;none&quot;
    },
    &quot;Beschlüsse&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Szenario 5: Ungültige Clientanfrage - Angabe leerer Ressourcen. {#bad-cl-req-empt-res-sp}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Deaktiviert/Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 412,
    &quot;code&quot;: &quot;missing_resource&quot;,
    &quot;message&quot;: &quot;Der Ressourcenparameter fehlt&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;none&quot;
    },
    &quot;Beschlüsse&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Szenario 6: Netzwerkfehler. {#ntwrk-error}

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;Beschlüsse&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;network_received_error&quot;,
    &quot;message&quot;: &quot;Beim Abrufen der Antwort vom zugehörigen Partnerdienst ist ein Lesefehler aufgetreten. Ein erneuter Versuch mit der Anfrage kann das Problem lösen.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;retry&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;autorisiert&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;network_received_error&quot;,
    &quot;message&quot;: &quot;Beim Abrufen der Antwort vom zugehörigen Partnerdienst ist ein Lesefehler aufgetreten. Ein erneuter Versuch mit der Anfrage kann das Problem lösen.&quot;
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot;: &quot;retry&quot;
    }
    }
    ]
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Szenario 7: Der Fluss zur Vorautorisierung wurde ohne gültige AuthN-Sitzung aufgerufen.

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Deaktiviert/Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0,
    &quot;code&quot;: &quot;authentication_session_missing&quot;,
    &quot;message&quot;: &quot;Die mit dieser Anfrage verknüpfte Authentifizierungssitzung konnte nicht abgerufen werden. Der Benutzer muss sich erneut mit einem unterstützten MVPD authentifizieren, um fortfahren zu können.&quot;
    &quot;action&quot;: &quot;authentication&quot;
    },
    &quot;Beschlüsse&quot;: []
    }
    
    &quot;

</td>
  </tr>
</tbody>
</table>



### Szenario 8: Der Vorautorisierungsfluss wurde vor Abschluss des setRequestor-Aufrufs aufgerufen

<table>
<thead>
  <tr>
    <th>Verbesserte Fehlercode-Markierung</th>
    <th>Reaktion</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Deaktiviert/Aktiviert</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0,
    &quot;code&quot;: &quot;requestor_not_configured&quot;,
    &quot;message&quot;: &quot;Der Anforderer ist noch nicht konfiguriert, was eine Voraussetzung für die Verwendung einer anderen API als der setRequestor-API ist.&quot;
    &quot;action&quot;: &quot;retry&quot;
    },
    &quot;Beschlüsse&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

