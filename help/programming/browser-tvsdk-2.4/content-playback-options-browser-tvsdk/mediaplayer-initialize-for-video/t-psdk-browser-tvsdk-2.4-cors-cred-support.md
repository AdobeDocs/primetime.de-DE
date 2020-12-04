---
description: Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.
seo-title: Ressourcenfreigabe über mehrere Herkünfte
title: Ressourcenfreigabe über mehrere Herkünfte
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Ressourcenfreigabe über mehrere Herkünfte {#cross-origin-resource-sharing}

Die Unterstützung des Attributs withCredentials in XMLHttpRequests ermöglicht die Cross-Herkunft Resource Sharing (CORS)-Anfragen, die Cookies der Zielgruppe-Domäne für verschiedene Anforderungstypen einzuschließen.

Wenn der Client ein Manifest, Segment oder einen Schlüssel anfordert, kann der Server ein Cookie setzen, das der Client für nachfolgende Anforderungen übergeben muss. Um das Lesen und Schreiben von Cookies zu ermöglichen, muss der Client das `withCredentials`-Attribut für Anforderungen mit mehreren Herkünfte auf `true` setzen.

So aktivieren Sie die `withCredentials`-Unterstützung für die meisten Anforderungstypen beim Abspielen einer bestimmten Medienressource:

1. Erstellen Sie das `CORSConfig`-Objekt.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Verbinden Sie das `corsConfig`-Objekt mit dem `NetworkConfiguration`-Objekt und setzen Sie `useCookieHeaderForAllRequests` auf `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Legen Sie `networkConfig` im `MediaPlayerItemConfig`-Objekt fest.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Übergeben Sie `MediaPlayerItemConfig` an die `MediaPlayer.replaceCurrentResource`-Methode.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>Das `useCookieHeaderForAllRequests`-Flag wirkt sich nicht auf Lizenzanforderungen aus. Um das `withCredentials`-Attribut für eine Lizenzanforderung auf `true` festzulegen, müssen Sie das `withCredentials`-Attribut in Ihren Schutzdaten oder einen Autorisierungsschlüssel in den `httpRequestHeaders` Ihrer Schutzdaten angeben. Beispiel:

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

Das Flag wirkt sich nicht auf eine Lizenzanforderung aus, da einige Server in ihrer Antwort das Feld `Access-Control-Allow-Origin` auf Platzhalter (&#39;*&#39;) setzen. Wenn das Berechtigungskennzeichen jedoch auf `true` gesetzt ist, kann der Platzhalter nicht in `Access-Control-Allow-Origin` verwendet werden. Wenn Sie `useCookieHeaderForAllRequests` für alle Anforderungstypen auf `true` setzen, wird möglicherweise der folgende Fehler für eine Lizenzanforderung angezeigt:

Beachten Sie die folgenden Informationen:

* Wenn ein Aufruf mit `withCredentials=true` fehlschlägt, wird der Aufruf von Browser TVSDK ohne `withCredentials` weitere Zustellversuche.
* Wenn ein Aufruf mit `networkConfiguration.useCookieHeaderForAllRequests=false` erfolgt, werden XHR-Anforderungen ohne das `withCredentials`-Attribut ausgeführt.