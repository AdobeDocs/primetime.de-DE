---
description: Um FairPlay Streaming in Ihre TVSDK-App zu implementieren, müssen Sie einen Resource Loader schreiben, der eine Lizenzakquise-Anfrage an Ihren FairPlay-Streaming-Server sendet.
title: Apple FairPlay in TVSDK-Anwendungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Apple FairPlay in TVSDK-Anwendungen  {#apple-fairplay-in-tvsdk-applications}

Um FairPlay Streaming in Ihre TVSDK-App zu implementieren, müssen Sie einen Resource Loader schreiben, der eine Lizenzakquise-Anfrage an Ihren FairPlay-Streaming-Server sendet.

Der Resource Loader-Code ist für die folgenden Aufgaben verantwortlich:

1. Legen Sie fest, wohin die Lizenzakquise-Anfrage gesendet werden soll.
1. Formatieren Sie die Anforderung.
1. Geben Sie die erforderlichen Informationen für den Server an, damit der Server entscheiden kann, ob die Anfrage zulässig sein soll.

Wenn Sie beispielsweise Adobe Primetime Cloud DRM mit ExpressPlay verwenden, sendet Ihr Resource Loader die Anfrage an:

```
https://fp-gen.service.expressplay.com
```

Der Resource Loader formatiert die Anforderung und hängt ein ExpressPlay-Token an, das die Wiedergabe an die URL autorisiert. Beim Erwerb des ExpressPlay-Tokens gibt es mehrere Optionen zu beachten. Diese Optionen werden durch das Verpacken des Inhalts bestimmt.

Beim Verpacken Ihres Inhalts wird der Packager eingefügt `skd:` URLs in Ihrem M3U8-Manifest. Nach dem `skd:` eingeben, können Sie alle Daten in das Manifest einfügen. Sie können diese Daten in Ihrem Anwendungscode verwenden, um die oben aufgeführten Aufgaben durchzuführen. Sie können beispielsweise `skd:{content_id}` damit Ihre App die ID des wiedergegebenen Inhalts ermitteln und ein Token für diesen bestimmten Inhalt anfordern kann. Sie können beispielsweise auch `skd:{entitlement_server_url}?cid={content_id}`, damit die URL des Berechtigungsservers für Ihre App nicht fest codiert werden muss.

Möglicherweise benötigen Sie keine Informationen in Ihrer `skd:` URL, wenn Sie beim Start der Wiedergabe die Inhalts-ID bereits über andere Kanäle kennen. Das zweite Beispiel ist eine ideale Lösung, um Ihre Einrichtung zu testen, Sie können sie aber auch in einer Produktionsumgebung verwenden.

>[!TIP]
>
>Sie bestimmen das Format von `skd:`.

Ihr Inhalt wird mithilfe der Variablen `skd:` -Protokoll, aber Ihre Lizenzanfrage verwendet `https:`. Die gängigsten Optionen für die Behandlung dieser Protokolle sind:

* **Anfangstest der End-to-End-Wiedergabe** Wählen Sie beim Verpacken Ihres Inhalts eine `skd:` URL. Wenn Sie Ihre App testen, erwerben Sie manuell eine Lizenz von ExpressPlay und codieren Sie die Lizenz (eine `https:` URL) und Inhalts-URL in Ihrem Lader.

  Beispiel:

  ```
  NSString* const PLAYLIST_URL =  
    @"https://{your_content_URL}/{your_manifest}.m3u8"; 
  NSString* const EXPRESSPLAY_TOKEN =  
    @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
      ExpressPlayToken={copy_your_token_to_here}";
  ```

* **Die meisten anderen Fälle** Wählen Sie beim Verpacken Ihres Inhalts eine `skd:` URL, die die Kennung des Inhalts eindeutig darstellt. Parsen Sie in Ihrem Lader die `skd:` URL, senden Sie es an Ihren Server, um ein Token zu erhalten, und verwenden Sie das resultierende Token als URL.

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

## Aktivieren von Apple FairPlay in TVSDK-Anwendungen{#enable-apple-fairplay-in-tvsdk-applications}

Sie können Apple FairPlay Streaming, die DRM-Lösung von Apple, in Ihre TVSDK-Anwendungen implementieren.

1. Erstellen Sie Ihren FairPlay-Kunden-Ressourcen-Loader durch Implementierung von `PTAVAssetResourceLoaderDelegate`.

   Weitere Informationen finden Sie unter [Apple FairPlay in TVSDK-Anwendungen](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie die Anweisungen im Abschnitt *Handbuch zum FairPlay Streaming-Programm* ( *FairPlayStreaming_PG.pdf*), die in [FairPlay Server SDK für die Entwicklung einer FPS-unterstützten App](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   Die `resourceLoader:shouldWaitForLoadingOfRequestedResource` -Methode entspricht dem in `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT]
   >
   >Um Inhalte wiederzugeben, ändern Sie im Szenario mit dem ExpressPlay-Lizenzserver das URL-Schema in der URL der Lizenzanfrage für den ExpressPlay-Server unter `skd://` nach `https://` (oder `https://`).

1. Registrieren *FairPlay* Customer Resource Loader mit `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Wenn Sie Ihren eigenen FairPlay-Lizenzserver geschrieben haben oder einen Drittanbieter-FairPlay-Lizenzserver verwenden, wenden Sie sich an Ihren Lizenzserver-Anbieter, um die URL, Formatierung und andere Anforderungen zu ermitteln.
