---
description: Die Berechtigungsanfrage und die Antwort werden über eine gegenseitig authentifizierte SSL-Verbindung zwischen dem Lizenzserver und dem Berechtigungsdienst des Kunden weitergeleitet.
title: SIEHE Öffentliche API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# SIEHE Öffentliche API {#sees-public-api}

Die Berechtigungsanfrage und die Antwort werden über eine gegenseitig authentifizierte SSL-Verbindung zwischen dem Lizenzserver und dem Berechtigungsdienst des Kunden weitergeleitet.

Das HTTPS-URI-Schema ( [https://tools.ietf.org/html/rfc7230#section-2.7.2](https://tools.ietf.org/html/rfc7230#section-2.7.2)) verwendet wird, um den Berechtigungs-Endpunkt und die HTTP-POST-Anforderungsmethode ( [https://tools.ietf.org/html/rfc7231#section-4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3)) für die Anfrage verwendet. Der Berechtigungs-Endpunkt sowie eine Markierung, die die Back-End-Berechtigung angibt, sind erforderlich und müssen während der Verpackung in die Richtlinie aufgenommen werden.

## Berechtigungsanfrage {#section_BFBFEF0795CA46D6842C479256B95F95}

Der Hauptteil der Berechtigungsanforderung ist ein JSON-Objekt, das wie unten dargestellt definiert ist.

**Definition des JSON-Berechtigungsanfrageobjekts**

```
{ 
 "title" : "Entitlement Request", 
 "type" : "object", 
 "properties" : { 
  "messageID" : { 
   "type" : "string", 
   "description" : "Unique ID for this message (GUID).  Used to confirm that the subsequent response is actually for this request." 
  }, 
  "version" : { 
   "type" : "integer", 
   "description" : "Version number of the protocol, currently 1." 
  }, 
  "requestType" : { 
   "type" : "integer", 
   "description" : "Request type. 1 - time based entitlement request, 2 - device registration entitlement request 3 - device bound entitlement request." 
  }, 
  "contentID" : { 
   "type" : "string", 
   "description" : "Content ID (GUID) that was given to the content during packaging time." 
  }, 
  "customerCookie" : { 
   "type" : "string", 
   "description" : "Customer cookie. Cookie is just arbitrary string up to 32 characters long." 
  } 
    }, 
 "required" : ["messageID", "version", "contentID"] 
}
```

## Antwort auf Berechtigungen {#section_F15A9FD6BAD946B3B4C5C14612F90154}

Der Hauptteil der Antwort auf die Berechtigung ist ein JSON-Objekt.

**Definition des JSON-Berechtigungsantwortobjekts**

```
{ 
  "title" : "Entitlement Response", 
  "type" : "object", 
  "properties" : { 
    "messageID" : { 
    "type" : "string", 
    "description" : "Unique ID from the Entitlement Request message.   
      Must match, or entitlement will be denied." 
  }, 
  "version" : { 
    "type" : "integer", 
    "description" : "Version number of the protocol; must be <= the version number  
      from the Entitlement Request message." 
  }, 
  "isAllowed" : { 
    "type" : "boolean", 
    "description" : "Grant the license or not." 
  }, 
  "epTokenURL" : { 
    "type" : "string", 
    "description" : "ExpressPlay Token URL" 
  }, 
  "error" : { 
    "type" : "integer", 
    "description" : "An error number produced by the entitlement server.  
      Will be passed to the client as the 'code' field of the server error response." 
  }, 
  "errorText" : { 
    "type" : "string", 
    "description" : "Additional error information produced by the entitlement server.  
      Will be passed to the client as the 'text' field of the server error response." 
  }, 
  "required" : ["messageID", "version", "isAllowed", "epTokenURL"] 
}
```
