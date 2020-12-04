---
description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-description: Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.
seo-title: Mit Cookies arbeiten
title: Mit Cookies arbeiten
uuid: 7586a5a7-9914-403b-86a9-fbdd28664b07
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Mit Cookies arbeiten{#work-with-cookies}

Sie können TVSDK verwenden, um beliebige Daten in Cookie-Headern für Sitzungsverwaltung, Gate-Zugriff usw. zu senden.

Hier ein Beispiel mit einer Art Authentifizierung bei Anforderungen an den Schlüsselserver:

1. Ihr Kunde meldet sich in einem Browser bei Ihrer Website an und seine Anmeldung zeigt, dass er Inhalte Ansicht haben darf.
1. Ihre Anwendung generiert ein Authentifizierungstoken, basierend auf den Erwartungen des Lizenzservers. Übergeben Sie diesen Wert an TVSDK.
1. TVSDK legt diesen Wert im Cookie-Header fest.
1. Wenn TVSDK eine Anforderung an den Schlüsselserver sendet, um einen Schlüssel zum Entschlüsseln des Inhalts abzurufen, enthält diese Anforderung den Authentifizierungswert im Cookie-Header, sodass der Schlüsselserver weiß, dass die Anforderung gültig ist.

So arbeiten Sie mit Cookies:

1. Verwenden Sie die Eigenschaft `cookieHeaders` in `NetworkConfiguration`, um ein Cookie zu setzen. Die `cookieHeaders`-Eigenschaft ist ein Metadatenobjekt. Sie können diesem Objekt Schlüsselwertpaare hinzufügen, die in die Cookie-Kopfzeile eingefügt werden sollen.

   Beispiel:

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Standardmäßig werden Cookie-Kopfzeilen nur mit Schlüsselanforderungen gesendet. Um Cookie-Kopfzeilen mit allen Anforderungen zu senden, setzen Sie die `NetworkConfiguration`-Eigenschaft `useCookieHeadersForAllRequests` auf true.

1. Um sicherzustellen, dass `NetworkConfiguration` funktioniert, legen Sie es als Metadaten fest:

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Geben Sie die Metadaten aus dem vorherigen Schritt an, wenn Sie ein `MediaResource` erstellen.

   Wenn Sie beispielsweise die `createFromURL`-Methode verwenden, geben Sie die folgenden Informationen ein:

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```

