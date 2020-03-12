---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-title: Mit Cookies arbeiten
title: Mit Cookies arbeiten
uuid: f060b520-ceec-48ca-929f-683566fe6ae7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mit Cookies arbeiten{#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.

Hier ein Beispiel mit einer Art Authentifizierung bei Anforderungen an den Schlüsselserver:

1. Ihr Kunde meldet sich in einem Browser bei Ihrer Website an und seine Anmeldung zeigt, dass er Inhalte Ansicht haben darf.
1. Ihre Anwendung generiert ein Authentifizierungstoken, basierend auf den Erwartungen des Lizenzservers. Übergeben Sie diesen Wert an TVSDK.
1. TVSDK legt diesen Wert im Cookie-Header fest.
1. Wenn TVSDK eine Anforderung an den Schlüsselserver sendet, um einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält diese Anforderung den Authentifizierungswert im Cookie-Header, sodass der Schlüsselserver weiß, dass die Anforderung gültig ist.

So arbeiten Sie mit Cookies:

1. Erstellen Sie eine `cookieManager` und fügen Sie Ihre Cookies für die URIs zu Ihrem `cookieStore`.

   Beispiel:

   >[!IMPORTANT]
   >
   >Wenn 302-Umleitungen aktiviert sind, kann die Anzeigenanforderung an eine Domäne weitergeleitet werden, die sich von der Domäne unterscheidet, zu der das Cookie gehört.

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDK Abfrage diesen cookieManager zur Laufzeit, prüft, ob mit der URL verknüpfte Cookies vorhanden sind, und verwendet diese automatisch.

   Eine andere Option ist die Verwendung `cookieHeaders` in, `NetworkConfiguration` um eine beliebige Cookie-Header-Zeichenfolge für Anforderungen festzulegen. Standardmäßig wird dieser Cookie-Header nur mit Schlüsselanforderungen gesendet. Um den Cookie-Header mit allen Anforderungen zu senden, verwenden Sie die `NetworkConfiguration` Methode `setUseCookieHeadersForAllRequests`:

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

