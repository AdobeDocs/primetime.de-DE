---
title: Details zum Richtlinien-Workflow
description: Details zum Richtlinien-Workflow
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# BEES-Workflow {#bees-workflow}

**Zusammenfassung:**

* **Politik** - Erstellen Sie eine DRM BEES-basierte Richtlinie, die anzeigt, dass BEES für alle mit dieser Richtlinie verpackten Inhalte erforderlich ist.
* **Verpackung** - Verpacken Sie Inhalte mithilfe der BEES-bezogenen DRM-Richtlinie.
* **Authentifizierung** - Authentifizieren Sie Ihr Client-Gerät und verwenden Sie die Primetime DRM-API oder die Primetime-API, um dieses Token mit Primetime Cloud DRM zu verknüpfen. Dadurch sendet das Client-Gerät dieses Authentifizierungstoken zusammen mit allen Lizenzanfragen an Primetime Cloud DRM. Primetime Cloud DRM verarbeitet dieses Token nicht, sondern übergibt es stattdessen (als undurchsichtigen Blob) zur Verarbeitung an Ihren BEES-Endpunkt.
* **Lizenzierung** - Fordern Sie eine Lizenz für Ihre geschützten Inhalte an. Das Client-Gerät hängt Ihr zuvor festgelegtes Authentifizierungstoken automatisch an den Aufruf an.
* **Berechtigung** - Primetime Cloud DRM ermittelt, ob der Inhalt mit einer Richtlinie gepackt wurde, die BEES erfordert. Primetime Cloud DRM erstellt eine JSON-Anfrage zum Senden an den BEES-Endpunkt. Die BEES-Antwort weist Primetime Cloud DRM an, ob eine Lizenz erteilt werden soll oder nicht, und optional, welche DRM-Richtlinie verwendet werden soll.

## Details zum Richtlinien-Workflow {#policy-workflow-details}

Wenn Primetime Cloud DRM eine Lizenzanfrage verarbeitet, analysiert es die DRM-Richtlinie in der Anfrage, um festzustellen, ob ein Aufruf an einen Backend-Berechtigungsdienst erforderlich ist, bevor der Inhalt angezeigt werden kann. Wenn ein BEES-Aufruf *is* erforderlich, erstellt Primetime Cloud DRM die BEES-Anfrage und analysiert dann die DRM-Richtlinie, um einen angegebenen BEES-URL-Endpunkt für die BEES-Anfrage zu erhalten.

Wenden Sie Ihre DRM-Richtlinie an, die die BEES-Anforderung anzeigt und die folgenden beiden benutzerdefinierten Eigenschaften in der Richtlinie angibt:

* `policy.customProp.1=bees.required=<true | false>`
* `policy.customProp.2=bees.url=<url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Verwenden Sie beispielsweise den Primetime DRM Policy Manager ( [!DNL AdobePolicyManager.jar]), geben Sie die beiden folgenden benutzerdefinierten Eigenschaften in der [!DNL flashaccesstools.properties] Konfigurationsdatei:

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Wenn Sie bereits `policy.customProp.1` oder `policy.customProp.2` für eine andere Eigenschaft verwenden Sie einfach eindeutige Zahlen für die neueren Eigenschaften.

## Package-Workflow-Details {#package-workflow-details}

Bei der Verpackung Ihres Adobe Access-geschützten Inhalts müssen Sie eine Ihrer BEES-bezogenen DRM-Richtlinien auf den Inhalt anwenden.

## Details zum Authentifizierungs-Workflow {#authentication-workflow-details}

Damit Ihr BEES-Endpunkt Berechtigungsentscheidungen treffen kann, muss das Client-Gerät Authentifizierungsinformationen bereitstellen. Dazu verwenden Sie Ihr eigenes kundenspezifisches Authentifizierungstoken.

Primetime Cloud DRM muss dieses Token nicht verstehen - es übergibt dieses Token einfach an Ihren BEES-Endpunkt. Das Client-Gerät ist für die Erstellung oder den Erwerb dieses Tokens und dessen Einstellung mithilfe der Variablen `DRMManager.setAuthenticationToken()` API.

Führen Sie die folgenden Schritte aus, um dieses Token mit Primetime Cloud DRM zu verknüpfen, damit es mit der Lizenzanfrage gesendet wird:

Instanziieren Sie die `DRMManager` -Objekt mit den DRM-Metadaten des Inhalts, der für Primetime Cloud DRM gepackt wurde.

Die `setAuthenticationToken()` -Methode funktioniert, indem das angegebene Byte-Array mit der Lizenzserver-URL verknüpft wird, die in den DRM-Metadaten bereitgestellt wurde, die zum Instanziieren verwendet wurden `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Das Token wird mit allen Lizenzanfragen gesendet, bis das Token durch Aufruf von geleert wird. `.setAuthenticationToken` , wobei null als Parameter angegeben wird.

## Details zum Lizenzarbeitsablauf{#license-workflow-details}

Fordern Sie eine Lizenz von Primetime Cloud DRM an, indem Sie `mgr.loadVoucher()`.

## Details zu Berechtigungsanfragen und Antworten{#entitlement-request-and-response-details}

Wenn Primetime Cloud DRM feststellt, dass der Inhalt mit einer BEES-bezogenen DRM-Richtlinie gepackt wurde, erstellt es die folgende JSON-Anfrage, die an den in der DRM-Richtlinie angegebenen BEES-Endpunkt gesendet wird:

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

Die folgende Antwort wird vom BEES-Endpunkt erwartet:

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

Primetime Cloud DRM verwendet die Antwort, um zu bestimmen, ob eine Lizenz für das anfordernde Gerät erteilt werden soll und ob eine neue DRM-Richtlinie im Lizenzgenerierungsprozess ersetzt werden soll. Wenn `isAllowed` is `true` und in der Antwort keine Richtlinie angegeben ist, wird die ursprüngliche DRM-Richtlinie verwendet, die während der Inhaltspaketdauer verwendet wird, um die Lizenz zu generieren.
