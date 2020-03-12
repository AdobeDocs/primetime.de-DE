---
description: Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.
seo-title: Ressourcenfreigabe über mehrere Herkünfte
title: Ressourcenfreigabe über mehrere Herkünfte
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Ressourcenfreigabe über mehrere Herkünfte {#cross-origin-resource-sharing}

Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.

Wenn der Client ein Manifest, Segment oder einen Schlüssel anfordert, kann der Server ein Cookie setzen, das der Client für nachfolgende Anforderungen übergeben muss. Um das Lesen und Schreiben von Cookies zu ermöglichen, muss der Client das `withCredentials` Attribut für Anforderungen mit `true` übergreifender Herkunft festlegen.

So aktivieren Sie beim Abspielen einer bestimmten Medienressource die `withCredentials` Unterstützung für die meisten Anforderungstypen:

1. Erstellen Sie das `CORSConfig` Objekt.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Hängen Sie das Objekt `corsConfig` an das `NetworkConfiguration` Objekt an und legen Sie `useCookieHeaderForAllRequests` den Wert `true`fest.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Wird `networkConfig` im `MediaPlayerItemConfig` Objekt eingestellt.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. An `MediaPlayerItemConfig` die `MediaPlayer.replaceCurrentResource` Methode übergeben.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>Das `useCookieHeaderForAllRequests` Flag wirkt sich nicht auf Lizenzanforderungen aus. Um das `withCredentials` Attribut `true` für eine Lizenzanforderung festzulegen, müssen Sie das `withCredentials` -Attribut in Ihren Schutzdaten oder einen Autorisierungsschlüssel in der `httpRequestHeaders` Ihrer Schutzdaten angeben. Beispiel:

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

Das Flag wirkt sich nicht auf eine Lizenzanforderung aus, da einige Server in ihrer Antwort das `Access-Control-Allow-Origin` Feld auf Platzhalter (&#39;*&#39;) setzen. Wenn das Berechtigungskennzeichen jedoch auf `true`festgelegt ist, kann der Platzhalter nicht in verwendet werden `Access-Control-Allow-Origin`. Wenn Sie `useCookieHeaderForAllRequests` für alle Anforderungstypen auf `true` einstellen, wird möglicherweise die folgende Fehlermeldung für eine Lizenzanforderung angezeigt:

Beachten Sie die folgenden Informationen:

* Wenn ein Aufruf mit `withCredentials=true` Fehler erfolgt, wird der Aufruf von Browser TVSDK ohne `withCredentials`Aufruf weitere Zustellversuche.
* Wenn ein Aufruf mit erfolgt `networkConfiguration.useCookieHeaderForAllRequests=false`, werden XHR-Anforderungen ohne das `withCredentials` Attribut ausgeführt.