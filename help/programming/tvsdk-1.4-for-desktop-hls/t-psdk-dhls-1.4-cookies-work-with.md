---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für die Sitzungsverwaltung, den Gate-Zugriff usw. zu senden.
title: Arbeiten mit Cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '234'
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

1. Verwenden Sie die `cookieHeaders` -Eigenschaft in `NetworkConfiguration` , um ein Cookie zu setzen. Die `cookieHeaders` -Eigenschaft ein Metadatenobjekt ist und Sie diesem Objekt Schlüsselwertpaare hinzufügen können, die in die Cookie-Kopfzeile aufgenommen werden sollen.

   Beispiel:

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Standardmäßig werden Cookie-Header nur mit Schlüsselanfragen gesendet. Um Cookie-Header mit allen Anforderungen zu senden, legen Sie die `NetworkConfiguration` property `useCookieHeadersForAllRequests` auf &quot;true&quot;.

1. Um sicherzustellen, dass `NetworkConfiguration` funktioniert, legen Sie es als Metadaten fest:

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Geben Sie die Metadaten aus dem vorherigen Schritt an, wenn Sie eine `MediaResource`.

   Wenn Sie beispielsweise die `createFromURL` -Methode die folgenden Informationen eingeben:

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```
