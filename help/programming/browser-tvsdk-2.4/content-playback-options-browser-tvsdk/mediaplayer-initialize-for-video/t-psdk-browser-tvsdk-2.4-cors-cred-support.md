---
description: Die Unterstützung für das Attribut withCredentials in XMLHttpRequests ermöglicht es CORS-Anfragen (Cross-Origin Resource Sharing), die Cookies der Zieldomäne für eine Vielzahl von Anfragetypen einzuschließen.
keywords: CORS; Cross Origin; Ressourcenfreigabe; Cookies; withCredentials
title: Cross-Origin Resource Sharing
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Cross-Origin Resource Sharing {#cross-origin-resource-sharing}

Die Unterstützung für das Attribut withCredentials in XMLHttpRequests ermöglicht es CORS-Anfragen (Cross-Origin Resource Sharing), die Cookies der Zieldomäne für eine Vielzahl von Anfragetypen einzuschließen.

Wenn der Client ein Manifest, ein Segment oder einen Schlüssel anfordert, kann der Server ein Cookie setzen, das der Client für nachfolgende Anforderungen übergeben muss. Damit Cookies gelesen und geschrieben werden können, muss der Client die `withCredentials` Attribut `true` für Anforderungen über die Herkunft hinweg.

Aktivieren `withCredentials` Unterstützung für die meisten Anforderungstypen bei der Wiedergabe einer bestimmten Medienressource:

1. Erstellen Sie die `CORSConfig` -Objekt.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Anfügen der `corsConfig` der `NetworkConfiguration` -Objekt und -set `useCookieHeaderForAllRequests` nach `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Satz `networkConfig` im `MediaPlayerItemConfig` -Objekt.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Pass `MediaPlayerItemConfig` der `MediaPlayer.replaceCurrentResource` -Methode.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>Die `useCookieHeaderForAllRequests` -Markierung hat keine Auswirkungen auf Lizenzanfragen. Um die `withCredentials` Attribut `true` für eine Lizenzanforderung müssen Sie die `withCredentials` -Attribut in Ihren Schutzdaten oder geben Sie einen Autorisierungsschlüssel in der `httpRequestHeaders` Ihrer Schutzdaten. Beispiel:

```
# Example 1 
{ 
    "com.widevine.alpha": {  
        "withCredentials":true,  
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i]" } 
} 
 
# Example 2 
{ 
    "com.widevine.alpha": { 
        "httpRequestHeaders": {  
            "authorization": "true"  
            }, 
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i>]" }
        } 
}
```

Das Flag wirkt sich nicht auf eine Lizenzanfrage aus, da einige Server die `Access-Control-Allow-Origin` Feld zum Platzhalter (&#39;&#42;&#39;) in ihrer Antwort. Wenn das Anmeldedaten-Flag jedoch auf `true`, kann der Platzhalter nicht in `Access-Control-Allow-Origin`. Wenn Sie `useCookieHeaderForAllRequests` nach `true` für alle Anforderungstypen wird möglicherweise der folgende Fehler bei einer Lizenzanfrage angezeigt:

Beachten Sie die folgenden Informationen:

* Wenn ein Aufruf mit `withCredentials=true` schlägt fehl, versucht das Browser TVSDK den Aufruf ohne `withCredentials`.
* Wenn ein Aufruf mit `networkConfiguration.useCookieHeaderForAllRequests=false`, werden XHR-Anfragen ohne die `withCredentials` -Attribut.
