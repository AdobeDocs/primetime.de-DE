---
seo-title: Details zum Richtlinienarbeitsablauf
title: Details zum Richtlinienarbeitsablauf
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# BEES-Workflow {#bees-workflow}

**Zusammenfassung:**

* **Richtlinie** - Erstellen Sie eine DRM BEES-basierte Richtlinie, die angibt, dass BEES für alle Inhalte, die mit dieser Richtlinie verpackt werden, erforderlich ist.
* **Verpacken** - Verpacken Sie Inhalte mit der DRM-Richtlinie, die mit BEES kompatibel ist.
* **Authentifizierung** : Authentifizieren Sie Ihr Clientgerät und verwenden Sie die Primetime DRM-API oder die Primetime-API, um dieses Token mit Primetime Cloud DRM zu verknüpfen. Dadurch sendet das Clientgerät dieses Authentifizierungstoken zusammen mit allen Lizenzanforderungen an Primetime Cloud DRM. Primetime Cloud DRM verarbeitet diesen Schlüssel nicht, sondern leitet ihn zur Verarbeitung (als undurchsichtiger Block) an Ihren BEES-Endpunkt weiter.
* **Lizenzierung** - Fordern Sie eine Lizenz für Ihre geschützten Inhalte an. Das Clientgerät hängt automatisch Ihr zuvor eingestelltes Authentifizierungstoken an den Aufruf an.
* **Berechtigung** - Primetime Cloud DRM ermittelt, ob der Inhalt mit einer Richtlinie gepackt wurde, die BEES erfordert. Primetime Cloud DRM erstellt eine JSON-Anfrage, die an den BEES-Endpunkt gesendet wird. Die BEES-Antwort teilt Primetime Cloud DRM mit, ob eine Lizenz erteilt werden soll oder nicht und welche DRM-Richtlinie verwendet werden soll.

## Details zum Richtlinienarbeitsablauf {#policy-workflow-details}

Wenn Primetime Cloud DRM eine Lizenzanforderung verarbeitet, analysiert es die DRM-Richtlinie in der Anforderung, um zu ermitteln, ob ein Aufruf eines Back-End-Berechtigungsdiensts erforderlich ist, bevor der Inhalt angezeigt werden kann. Wenn ein BEES-Aufruf erforderlich *ist* , erstellt Primetime Cloud DRM die BEES-Anforderung und analysiert dann die DRM-Richtlinie, um einen angegebenen BEES-URL-Endpunkt für die BEES-Anforderung zu erhalten.

Wenden Sie Ihre DRM-Richtlinie an, die die BEES-Anforderung angibt, und geben Sie die folgenden zwei benutzerdefinierten Eigenschaften in der Richtlinie an:

    * `policy.customProp.1=bees.required=&lt;true| false>`
    * `policy.customProp.2=bees.url=&lt;url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Beispielsweise würden Sie mit dem Primetime DRM Policy Manager ( [!DNL AdobePolicyManager.jar]) die folgenden zwei benutzerdefinierten Eigenschaften in der [!DNL flashaccesstools.properties] Konfigurationsdatei angeben:

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Wenn Sie bereits eine `policy.customProp.1` oder `policy.customProp.2` eine andere Eigenschaft verwenden, verwenden Sie einfach eindeutige Zahlen für die neueren Eigenschaften.

## Details zum Paketarbeitsablauf {#package-workflow-details}

Beim Verpacken Ihrer Adobe Access-geschützten Inhalte müssen Sie eine Ihrer BEES-bezogenen DRM-Richtlinien auf die Inhalte anwenden.

## Details zum Authentifizierungsarbeitsablauf {#authentication-workflow-details}

Damit Ihr BEES-Endpunkt Berechtigungsentscheidungen treffen kann, muss das Client-Gerät Authentifizierungsinformationen bereitstellen. Dazu verwenden Sie Ihr eigenes kundenspezifisches Authentifizierungstoken.

Primetime Cloud DRM muss dieses Token nicht verstehen - es gibt dieses Token einfach an Ihren BEES-Endpunkt weiter. Das Clientgerät ist dafür verantwortlich, dass dieses Token erstellt oder erworben und mithilfe der `DRMManager.setAuthenticationToken()` API festgelegt wird.

Führen Sie die folgenden Schritte aus, um dieses Token mit Primetime Cloud DRM zu verknüpfen, damit es mit der Lizenzanforderung gesendet wird:

Instanziieren Sie das `DRMManager` Objekt mit den DRM-Metadaten des Inhalts, der für Primetime Cloud DRM verpackt wurde.

Die `setAuthenticationToken()` Methode funktioniert, indem das angegebene Byte-Array mit der Lizenzserver-URL verknüpft wird, die in den DRM-Metadaten angegeben ist, die zur Instanziierung verwendet wurden `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Das Token wird mit allen Lizenzanforderungen gesendet, bis das Token durch Aufruf `.setAuthenticationToken` mit null als Parameter geleert wird.

## Details zum Lizenzarbeitsablauf{#license-workflow-details}

Fordern Sie eine Lizenz von Primetime Cloud DRM an, indem Sie `mgr.loadVoucher()`anrufen.

## Details zu Berechtigungsanfragen und Antworten{#entitlement-request-and-response-details}

Wenn Primetime Cloud DRM feststellt, dass Inhalte mit einer DRM-Richtlinie mit BEES-Unterstützung verpackt wurden, erstellt es die folgende JSON-Anforderung, die an den in der DRM-Richtlinie angegebenen BEES-Endpunkt gesendet werden soll:

```
{
    "title":"Entitlement Request",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"Unique ID for this message. Used to confirm that the
                           returned response is for this particular message."
        },
        "version": {
            "type":"string",
            "description":"BEES Request Version. Currently 1."
        },
        "contentID": {
            "type":"string",
            "description":"Content ID (GUID)"
        },
        "customerSpecificAuthToken": {
            "type":"string",
            "description":"Base64-encoded authentication token. Must be set
                           explicitly by client before making the license request."
        }
    },
    "required": [
        "messageID",
        "version",
        "contentID"
    ]
}
```

Folgende Antwort wird vom BEES-Endpunkt erwartet:

```
{
    "title":"Entitlement Response",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"ID of the Entitlement Request that this Response is
                           handling. Must exactly match the ID of the request
                           or this response will be rejected."
        },
        "version": {
            "type":"string",
            "description":"BEES Response Version. Currently 1."
        },
        "isAllowed": {
            "type":"boolean",
            "description":"Grant the license or not."
        },
        "policy": {
            "type":"string",
            "description":"Base64-encoded policy to enforce  If no policy is
                           provided, the policy that was packaged with the content
                           during packaging time will be used to generate the license."
        },
        "error": {
            "type":"integer",
            "description":"An error number produced by the entitlement server.
                           Will be passed to the client as the 'code' field of
                           the server error response."
        },
        "errorText": {
            "type":"string",
            "description":"Additional error information produced by the
                           entitlement server. Will be passed to the client as
                           the 'text' field of the server error response."
        }
    },
    "required": [
        "messageID",
        "version",
        "isAllowed"
    ]
}
```

Primetime Cloud DRM verwendet die Antwort, um zu ermitteln, ob eine Lizenz für das anfordernde Gerät erteilt werden soll und ob eine neue DRM-Richtlinie im Lizenzgenerierungsvorgang ersetzt werden sollte. Wenn `isAllowed` dies der Fall ist `true` und in der Antwort keine Richtlinie angegeben ist, wird die ursprüngliche DRM-Richtlinie, die während der Inhaltspaketerstellung verwendet wird, zur Erstellung der Lizenz verwendet.