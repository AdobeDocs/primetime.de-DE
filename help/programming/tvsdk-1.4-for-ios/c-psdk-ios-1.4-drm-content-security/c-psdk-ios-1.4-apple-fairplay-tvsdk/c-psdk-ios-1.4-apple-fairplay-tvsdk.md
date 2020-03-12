---
description: Um FairPlay-Streaming in Ihre TVSDK-App zu implementieren, müssen Sie einen Resource Loader schreiben, der eine Lizenzanfrage an Ihren FairPlay Streaming-Server sendet.
seo-description: Um FairPlay-Streaming in Ihre TVSDK-App zu implementieren, müssen Sie einen Resource Loader schreiben, der eine Lizenzanfrage an Ihren FairPlay Streaming-Server sendet.
seo-title: Apple FairPlay in TVSDK-Anwendungen
title: Apple FairPlay in TVSDK-Anwendungen
uuid: 4384d379-37cd-46c5-8c25-0cda16bdebb8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Apple FairPlay in TVSDK-Anwendungen {#apple-fairplay-in-tvsdk-applications}

Um FairPlay-Streaming in Ihre TVSDK-App zu implementieren, müssen Sie einen Resource Loader schreiben, der eine Lizenzanfrage an Ihren FairPlay Streaming-Server sendet.

Der Resource Loader-Code ist für die folgenden Aufgaben verantwortlich:

1. Bestimmen Sie, wo die Lizenzanfrage gesendet werden soll.
1. Formatieren Sie die Anforderung.
1. Geben Sie die erforderlichen Informationen an den Server weiter, damit der Server entscheiden kann, ob die Anforderung zulässig sein soll.

Wenn Sie z. B. mit dem ExpressPlay-basierten Adobe Primetime Cloud DRM arbeiten, sendet Ihr Resource Loader die Anforderung an:

```
https://fp-gen.service.expressplay.com
```

Der Resource Loader formatiert die Anforderung und hängt ein ExpressPlay-Token an, das die Wiedergabe an die URL autorisiert. Beim Erwerb des ExpressPlay-Tokens stehen verschiedene Optionen zur Verfügung. Diese Optionen werden durch das Verpacken der Inhalte bestimmt.

Wenn Sie Ihren Inhalt verpacken, fügt der Packager `skd:` URLs in Ihr M3U8-Manifest ein. Nach dem `skd:` Eintrag können Sie alle Daten in das Manifest. Sie können diese Daten in Ihrem Anwendungscode verwenden, um die oben aufgeführten Aufgaben abzuschließen. Sie können beispielsweise verwenden, `skd:{content_id}` damit Ihre App die ID des wiedergegebenen Inhalts ermitteln und ein Token für dieses bestimmte Inhaltselement anfordern kann. Sie können zum Beispiel auch verwenden, `skd:{entitlement_server_url}?cid={content_id}`damit die URL des Berechtigungsservers für Ihre App nicht fest codiert werden muss.

Möglicherweise benötigen Sie keine Informationen in Ihrer `skd:` URL, wenn Sie bei der Wiedergabe von Beginn die Inhalts-ID bereits über andere Kanal kennen. Das zweite Beispiel ist eine ideale Lösung, um Ihr Setup zu testen, Sie können es aber auch in einer Produktions-Umgebung verwenden.

>[!TIP]
>
>Sie bestimmen das Format von `skd:`.

Ihr Inhalt wird mithilfe des `skd:` Protokolls abgerufen, aber Ihre Lizenzanforderung verwendet `https:`. Die häufigsten Optionen für den Umgang mit diesen Protokollen sind:

* **Anfänglicher Test der End-to-End-Wiedergabe** Wählen Sie beim Verpacken des Inhalts eine `skd:` URL aus. Erwerben Sie beim Testen Ihrer App manuell eine Lizenz von ExpressPlay und programmieren Sie die Lizenz (eine `https:` URL) und die Inhalts-URL in Ihrem Lader fest.

   Beispiel:

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **In den meisten anderen Fällen** wählen Sie beim Verpacken Ihres Inhalts eine URL aus, die die ID des Inhalts eindeutig `skd:` darstellt. Parsen Sie in Ihrem Lader die `skd:` URL, senden Sie sie an Ihren Server, um ein Token zu erwerben, und verwenden Sie das resultierende Token als URL.

   Beispiel:

   ```
   - (BOOL)resourceLoader:(AVAssetResourceLoader *)resourceLoader  
         shouldWaitForLoadingOfRequestedResource:(AVAssetResourceLoadingRequest *)loadingRequest { 
       NSURL *url = [[loadingRequest request] URL]; 
       if (![[url scheme] isEqual:@"skd"]) 
           return NO; 
   
       NSString *strUrl = [url absoluteString]; 
       NSLog(@"url is: %@", strUrl); 
   
       strUrl = [strUrl stringByReplacingOccurrencesOfString:@"skd://" withString:@"https://"]; 
   
       NSData *assetId; 
   
       NSData *requestBytes; 
       NSError* error = nil; 
       BOOL handled = NO; 
   
       NSData  *responseData = nil; 
   
       assetId = getMyAssetIdentifierFromURL(url); 
   
       /* Usecase 1: "On Premise Fairplay Server" 
        * Set the strUrl to the OnPremise Fairplay Server Url. The OnPremise Fairplay  
        * Server Url is either hardcoded in the App or derived from strUrl. 
        */ 
   #if 0  
       // Insert your use case 1 codes here: 
       // strUrl = getOnPremiseServerUrl(strUrl, assetId); 
   #endif // 
   
       /* Usecase 2: The strUrl is the entitlement server. 
        * Send assetId to the entitlement server; if the user is allowed to playback  
        * the content, the entitlement server will send back an ExpressPlay Token Url. 
        */ 
   
   #if 0 
       // The hardcoded SEES server: 
       strUrl = @"https://10.0.248.85:8080/sees/SEESServlet"; 
   
       // You can use the following code to simulate a device binding entitlement  
       // request:  
       // First, invoke getExpressPlayTokenUrlFromEntilementServer with  
       // bEnforceDeviceID set to false. When you play the content, the device_id  
       // will be registered on the ExpressPlay Server.  Now change code to set  
       // bEnforceDeviceID to true, and rerun the program. The ExpressPlay token  
       // sent back by the SEES server will be device bound. 
   
       // The strUrl returned below is the ExpressPlay Token URL. 
       strUrl = getExpressPlayTokenUrlFromEntilementServer(strUrl, assetId, true, &error); 
   #endif 
   
       /* Usecase 3: The strUrl is already the ExpressPlay Token Url. 
        */ 
   
       // Read in the certificate 
       NSLog(@"Get Application Certificate"); 
       NSString* certPath = [[NSBundle mainBundle] pathForResource:@"my_certificate.cer"  
                                                            ofType:nil]; 
   
       NSData *appCert = [NSData dataWithContentsOfFile:certPath]; 
   
       // To create the request blob for the server: 
       requestBytes = [loadingRequest streamingContentKeyRequestDataForApp: appCert 
                                                         contentIdentifier:assetId  
                                                                   options:nil  
                                                                     error:&error]; 
       if (requestBytes == nil) { 
           NSLog(@"Error creating server request: %@", error); 
           return false; 
       } 
       // Per the specification, send requestBytes along with the assetId to the Key 
       // Server and obtain the response. 
       NSError *err; 
   
       responseData = getCKCFromExpressPlayService( strUrl, requestBytes, assetId, &err); 
   
       if (responseData != nil) { 
           NSLog(@"Get response data: "); 
           [loadingRequest finishLoadingWithResponse:nil  
                                                data:(NSData *)responseData 
                                            redirect:nil]; 
       } 
       else { 
           [loadingRequest finishLoadingWithError:err]; 
           NSLog(@"bad key response"); 
       } 
       handled = YES; 
   bail: 
       return handled; 
   
   }
   ```

## Apple FairPlay in TVSDK-Anwendungen aktivieren{#enable-apple-fairplay-in-tvsdk-applications}

Sie können Apple FairPlay Streaming, die DRM-Lösung von Apple, in Ihren TVSDK-Anwendungen implementieren.

1. Erstellen Sie Ihren FairPlay-Kunden-Ressourcen-Loader durch Implementierung `PTAVAssetResourceLoaderDelegate`.

   Weitere Informationen finden Sie unter [Apple FairPlay in TVSDK-Anwendungen](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die Anweisungen im *FairPlay Streaming Programm Guide* ( *FairPlayStreaming_PG.pdf*) befolgen, das im [FairPlay Server SDK für die Entwicklung einer FPS-Aware-App](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)enthalten ist.

   Die `resourceLoader:shouldWaitForLoadingOfRequestedResource` Methode entspricht dem, was darin enthalten ist `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT] {important=&quot;high&quot;}
   >
   >Um Inhalte wiederzugeben, ändern Sie im Szenario mit dem ExpressPlay-Lizenzserver das URL-Schema in der URL Ihrer ExpressPlay-Server-Lizenzanfrage von `skd://` in `https://` (oder `https://`).

1. Registrieren Sie den *FairPlay* Customer Resource Loader mit `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Wenn Sie einen eigenen FairPlay-Lizenzserver geschrieben haben oder einen FairPlay-Lizenzserver eines Drittanbieters verwenden, wenden Sie sich an Ihren Lizenzserver-Anbieter, um die URL, Formatierung und andere Anforderungen für Ihren Lizenzserver zu ermitteln.