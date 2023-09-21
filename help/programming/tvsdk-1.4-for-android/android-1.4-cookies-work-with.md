---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.
title: Arbeiten mit Cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Arbeiten mit Cookies{#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.

Im Folgenden finden Sie ein Beispiel mit einer Art Authentifizierung bei Anforderungen an den Schlüsselserver:

1. Ihr Kunde meldet sich in einem Browser bei Ihrer Website an und seine Anmeldung zeigt an, dass er Inhalte anzeigen darf.
1. Ihre Anwendung generiert ein Authentifizierungstoken, das auf den Erwartungen des Lizenzservers basiert. Übergeben Sie diesen Wert an TVSDK.
1. TVSDK legt diesen Wert in der Cookie-Kopfzeile fest.
1. Wenn TVSDK eine Anfrage an den Schlüsselserver sendet, um einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält diese Anfrage den Authentifizierungswert im Cookie-Header, sodass der Schlüsselserver weiß, dass die Anfrage gültig ist.

So arbeiten Sie mit Cookies:

1. Erstellen Sie eine `cookieManager` und fügen Sie Ihre Cookies für die URIs zu Ihren `cookieStore`.

   Beispiel:

   >[!IMPORTANT]
   >
   >Wenn die Weiterleitung von 302 aktiviert ist, kann die Anzeigenanforderung an eine Domäne umgeleitet werden, die sich von der Domäne unterscheidet, zu der das Cookie gehört.

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDK fragt diesen CookieManager zur Laufzeit ab, prüft, ob der URL Cookies zugeordnet sind, und verwendet diese automatisch.

   Eine weitere Option ist die Verwendung von `cookieHeaders` in `NetworkConfiguration` , um eine beliebige Cookie-Header-Zeichenfolge festzulegen, die für Anfragen verwendet werden soll. Standardmäßig wird dieser Cookie-Header nur mit Schlüsselanfragen gesendet. Um den Cookie-Header mit allen Anforderungen zu senden, verwenden Sie die `NetworkConfiguration` method `setUseCookieHeadersForAllRequests`:

```java
   NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
    
   Metadata cookie = new MetadataNode(); 
   cookie.setValue("reqPayload", “1234567”); 
   networkConfiguration.setCookieHeaders(cookie); 
   networkConfiguration.setUseCookieHeadersForAllRequests( true ); 
    
   // Set NetworkConfiguration as Metadata:                                                                   
   MetadataNode resourceMetadata = new MetadataNode(); 
   resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                            networkConfiguration); 
    
   // Call MediaResource.createFromURL to set the metadata: 
   MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
   // Load the resource 
   mediaPlayer.replaceCurrentItem(resource);
```
