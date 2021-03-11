---
description: Sie können Apple FairPlay Streaming, die DRM-Lösung von Apple, in Ihren TVSDK-Anwendungen implementieren.
title: Apple FairPlay in TVSDK-Anwendungen aktivieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Apple FairPlay in TVSDK-Anwendungen aktivieren{#enable-apple-fairplay-in-tvsdk-applications}

Sie können Apple FairPlay Streaming, die DRM-Lösung von Apple, in Ihren TVSDK-Anwendungen implementieren.

1. Erstellen Sie Ihren FairPlay-Kunden-Ressourcen-Loader, indem Sie `PTAVAssetResourceLoaderDelegate` implementieren.

   Weitere Informationen finden Sie unter [Apple FairPlay in TVSDK-Anwendungen](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die Anweisungen im Handbuch *FairPlay Streaming Programm Guide* ( *FairPlayStreaming_PG.pdf*) befolgen, das im [FairPlay Server SDK für die Entwicklung einer FPS-Aware-App](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip) enthalten ist.

   Die `resourceLoader:shouldWaitForLoadingOfRequestedResource`-Methode entspricht dem unter `AVAssetResourceLoaderDelegate` angegebenen Wert.

   >[!IMPORTANT]
   >
   >Um Inhalte wiederzugeben, ändern Sie im Szenario mit dem ExpressPlay-Lizenzserver das URL-Schema in der URL Ihrer ExpressPlay FairPlay-Serverlizenzanforderung von `skd://` in `https://` (oder `https://`).

1. Registrieren Sie den *FairPlay* Customer Resource Loader mit `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Wenn Sie einen eigenen FairPlay-Lizenzserver geschrieben haben oder einen FairPlay-Lizenzserver eines Drittanbieters verwenden, wenden Sie sich an Ihren Lizenzserver-Anbieter, um die URL, Formatierung und andere Anforderungen für Ihren Lizenzserver zu ermitteln.
