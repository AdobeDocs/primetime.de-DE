---
description: 'null'
seo-description: 'null'
seo-title: Verwenden von DRMContentData zum Vorausladen von Lizenzen
title: Verwenden von DRMContentData zum Vorausladen von Lizenzen
uuid: 5cedd077-0613-4677-8fb0-81237d7ac61a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verwenden von DRMContentData zum Vorausladen von Lizenzen{#using-drmcontentdata-to-pre-load-licenses}

Die folgenden Schritte beschreiben den Arbeitsablauf zum Vorausfüllen der Lizenzierung für eine geschützte Mediendatei mit einem `DRMContentData` Objekt.

1. Rufen Sie die binären DRM-Metadaten für den gepackten Inhalt ab.

   Bei Verwendung des Primetime DRM Java Reference Implementierungs Packager wird diese Metadatendatei automatisch mit einer [!DNL .metadata] Erweiterung generiert. Sie können diese Metadaten beispielsweise mit der `URLLoader` Klasse herunterladen. Bei Verwendung von HLS- oder HDS-Inhalten werden die Metadaten in der Inhaltsmanifestdatei ( [!DNL .m3u8] oder [!DNL .f4m]) referenziert oder *in der Manifestdatei als Base64-kodierte Zeichenfolge enthalten* (die vor dem Verzehr Base64-dekodiert werden muss).
1. Erstellen Sie ein `DRMContentData` Objekt und übergeben Sie die Metadaten an die Konstruktorfunktion:

   ```
   var drmData:DRMContentData = new DRMContentData( metadata );
   ```

1. Die übrigen Schritte sind mit dem unter *Inhaltsschutzdetails* beschriebenen Arbeitsablauf identisch.

<!--<a id="example_EBEDA8E10F6344CABA4DE31DC342B8F8"></a>-->

```
import flash.events.DRMAuthenticationCompleteEvent; 
import flash.events.DRMAuthenticationErrorEvent; 
import flash.events.DRMErrorEvent; 
import flash.events.DRMStatusEvent; 
import flash.events.NetStatusEvent; 
import flash.net.NetConnection; 
import flash.net.Primetime; 
import flash.net.PrimetimePlayOptions; 
import flash.net.drm.AuthenticationMethod; 
import flash.net.drm.DRMContentData; 
import flash.net.drm.DRMManager; 
import flash.net.drm.LoadVoucherSetting; 
  
public class DRMPreloader extends Sprite  { 
    private var videoURL:String = "app-storage:/video.flv"; 
    private var userName:String = "user"; 
    private var password:String = "password"; 
    private var preloadConnection:NetConnection; 
    private var preloadStream:Primetime; 
    private var drmManager:DRMManager = DRMManager.getDRMManager(); 
 
    private var drmContentData:DRMContentData; 
 
    public function DRMPreloader():void { 
        drmManager.addEventListener(  
          DRMAuthenticationCompleteEvent.AUTHENTICATION_COMPLETE,  
          onAuthenticationComplete 
        ); 
        drmManager.addEventListener( 
          DRMAuthenticationErrorEvent.AUTHENTICATION_ERROR,  
          onAuthenticationError 
        ); 
        drmManager.addEventListener( 
          DRMStatusEvent.DRM_STATUS, onDRMStatus); 
        drmManager.addEventListener( 
          DRMErrorEvent.DRM_ERROR, onDRMError); 
        preloadConnection = new NetConnection(); 
        preloadConnection.addEventListener( 
          NetStatusEvent.NET_STATUS, onConnect); 
        preloadConnection.connect(null);  
    } 
 
    private function onConnect( event:NetStatusEvent ):void {  
        preloadMetadata(); 
    } 
 
    private function preloadMetadata():void {  
        preloadStream = new Primetime( preloadConnection ); 
        preloadStream.client = this; 
        var options:PrimetimePlayOptions = new PrimetimePlayOptions(); 
        options.streamName = videoURL; 
        preloadStream.preloadEmbeddedData( options );  
    }  
 
    public function onDRMContentData( drmMetadata:DRMContentData ):void {  
        drmContentData = drmMetadata; 
        if ( drmMetadata.authenticationMethod ==  
               AuthenticationMethod.USERNAME_AND_PASSWORD ) {  
            authenticateUser(); 
        } 
        else {  
            getVoucher(); 
        } 
    } 
 
    private function getVoucher():void {  
        drmManager.loadVoucher(  
          drmContentData,  
          LoadVoucherSetting.ALLOW_SERVER  
        ); 
    } 
 
    private function authenticateUser():void {  
        drmManager.authenticate(  
          drmContentData.serverURL,  
          drmContentData.domain,  
          userName,  
          password  
        ); 
    } 
 
    private function onAuthenticationError(  
      event:DRMAuthenticationErrorEvent ):void {  
        trace( "Authentication error: " +  
               event.errorID + ", " +  
               event.subErrorID ); 
    } 
 
    private function onAuthenticationComplete(  
      event:DRMAuthenticationCompleteEvent ):void {  
        trace( "Authenticated to: " +  
               event.serverURL + ",  
               domain: " +  
               event.domain ); 
        getVoucher(); 
    } 
 
    private function onDRMStatus( event:DRMStatusEvent ):void { 
        trace( "DRM Status: " + event.detail); 
        trace("--License allows offline playback = " +  
              event.isAvailableOffline ); 
        trace("--License already cached = " +  
              event.isLocal ); 
        trace("--License required authentication = " +  
              !event.isAnonymous ); 
    } 
 
    private function onDRMError( event:DRMErrorEvent ):void { 
        trace( "DRM error event: " +  
               event.errorID + ", " +  
               event.subErrorID + ", " +  
               event.text ); 
    } 
 
    public function onPlayStatus( info:Object ):void { 
        preloadStream.close(); 
    }  
} 
```

