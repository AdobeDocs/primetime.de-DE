---
description: Der Flash Runtime TVSDK benötigt ein signiertes Token, um zu überprüfen, ob Sie berechtigt sind, die TVSDK-API in der Domäne aufzurufen, in der sich Ihre Anwendung befindet.
seo-description: Der Flash Runtime TVSDK benötigt ein signiertes Token, um zu überprüfen, ob Sie berechtigt sind, die TVSDK-API in der Domäne aufzurufen, in der sich Ihre Anwendung befindet.
seo-title: Signiertes Token laden
title: Signiertes Token laden
uuid: 8760eab3-3d6d-47c6-9aa7-f64f6aa5ddcf
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Signiertes Token {#load-your-signed-token} laden

Der Flash Runtime TVSDK benötigt ein signiertes Token, um zu überprüfen, ob Sie berechtigt sind, die TVSDK-API in der Domäne aufzurufen, in der sich Ihre Anwendung befindet.

1. Besorgen Sie sich ein signiertes Token von Ihrem Kundenbetreuer für jede Ihrer Domänen (wobei jede Domäne eine bestimmte Domäne oder Wildcard-Domäne sein kann).

       Um ein Token zu erhalten, geben Sie entweder Adobe über die Domäne, in der Ihre Anwendung gespeichert oder geladen wird, oder vorzugsweise über die Domäne als SHA256-Hash. Im Gegenzug gibt Ihnen Adobe für jede Domäne ein unterschriebenes Token. Diese Token haben eine der folgenden Formen:
   
   * Eine [!DNL .xml]-Datei, die als Token für eine einzelne Domäne oder Wildcard-Domäne fungiert.

      >[!NOTE]
      >
      >Ein Token für eine Wildcard-Domäne deckt diese Domäne und alle zugehörigen Subdomänen ab. Beispielsweise würde ein Platzhalter-Token für die Domäne [!DNL mycompany.com] auch für [!DNL vids.mycompany.com] und [!DNL private.vids.mycompany.com] gelten; ein Platzhaltertoken für [!DNL vids.mycompany.com] würde auch [!DNL private.vids.mycompany.com] abdecken. *Platzhalterdomänentoken werden nur für bestimmte Flash Player unterstützt.*

   * Eine [!DNL .swf]-Datei mit Token-Informationen für mehrere Domänen (ohne Platzhalter) (Einzel- oder Platzhalterdaten), die Ihre Anwendung dynamisch laden kann.

1. Speichern Sie die Token-Datei am selben Speicherort oder in der gleichen Domäne wie Ihre Anwendung.

   Standardmäßig sucht TVSDK nach dem Token an diesem Speicherort. Alternativ können Sie den Namen und Speicherort des Tokens in `flash_vars` in Ihrer HTML-Datei angeben.
1. Wenn Ihre Tokendatei eine einzelne XML-Datei ist:
   1. Verwenden Sie `utils.AuthorizedFeaturesHelper.loadFrom`, um die unter der angegebenen URL gespeicherten Daten (die Tokendatei) herunterzuladen und die `authorizedFeatures`-Informationen daraus zu extrahieren.

      Dieser Schritt kann unterschiedlich sein. Sie können beispielsweise eine Authentifizierung durchführen, bevor Sie die Anwendung starten, oder Sie erhalten das Token direkt vom Content-Management-System (CMS).

   1. TVSDK löst ein `COMPLETED`-Ereignis aus, wenn die Belastung erfolgreich ist, oder ein `FAILED`-Ereignis, wenn dies nicht der Fall ist. Gehen Sie beim Erkennen eines Ereignisses entsprechend vor.

      Dies muss erfolgreich sein, damit Ihre Anwendung die erforderlichen `authorizedFeatures`-Objekte in Form eines `MediaPlayerContext`-Objekts für TVSDK bereitstellen kann.
   Dieses Beispiel zeigt, wie Sie eine Datei mit einem einzelnen Token [!DNL .xml] verwenden können.

   ```
   private function loadDirectTokenURL():void { 
       var url:String = constructAuthorizedFeatureTokenURL(); 
       _logger.debug("#onApplicationComplete Loading token from [{0}].", url); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE,  
           onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR,  
           onFeatureError); 
        _authorizedFeatureHelper.loadFrom(url); 
    }
   ```

1. Wenn Ihr Token eine [!DNL .swf]-Datei ist:
   1. Definieren Sie eine `Loader`-Klasse, um die [!DNL .swf]-Datei dynamisch zu laden.
   1. Legen Sie `LoaderContext` fest, um das Laden in der aktuellen Anwendungsdomäne anzugeben, wodurch TVSDK das richtige Token in der Datei [!DNL .swf] auswählen kann. Wenn `LoaderContext` nicht angegeben ist, wird standardmäßig `Loader.load` die .swf-Datei in die untergeordnete Domäne der aktuellen Domäne geladen.
   1. Suchen Sie nach dem VOLLSTÄNDIGEN Ereignis, das TVSDK auslöst, wenn die Belastung erfolgreich ist.

      Suchen Sie auch nach dem FEHLER-Ereignis und ergreifen Sie entsprechende Maßnahmen.
   1. Wenn die Belastung erfolgreich ist, verwenden Sie `AuthorizedFeaturesHelper`, um ein `ByteArray` zu erhalten, das die PCKS-7-kodierten Sicherheitsdaten enthält.

      Diese Daten werden über die AVE V11-API verwendet, um eine Autorisierungsbestätigung vom Flash Runtime Player zu erhalten. Wenn das Byte-Array keinen Inhalt hat, verwenden Sie stattdessen das Verfahren, um nach einer Tokendatei mit einer einzigen Domäne zu suchen.
   1. Verwenden Sie `AuthorizedFeatureHelper.loadFeatureFromData`, um die erforderlichen Daten aus dem Bytearray abzurufen.
   1. Entladen Sie die Datei [!DNL .swf].

   Die folgenden Beispiele zeigen, wie Sie eine Datei mit mehreren Token [!DNL .swf] verwenden können.

   **Beispiel 1 für mehrere Token:**

   ```
   private function onApplicationComplete(event:FlexEvent):void { 
       var url:String = constructAuthorizedFeatureTokenURLFromSwf();   
       _loader = new Loader(); 
       var swfUrl:URLRequest = new URLRequest(url); 
       var loaderContext:LoaderContext =  
           new LoaderContext(false, ApplicationDomain.currentDomain, null); 
       _loader.contentLoaderInfo.addEventListener(Event.COMPLETE,  
           modEventHandler); 
       _loader.contentLoaderInfo.addEventListener(IOErrorEvent.IO_ERROR,  
           errEventHandler); 
       _loader.contentLoaderInfo.addEventListener(ProgressEvent.PROGRESS,  
           onProgressHandler); 
       _loader.uncaughtErrorEvents.addEventListener(UncaughtErrorEvent. 
           UNCAUGHT_ERROR, uncaughtEventHandler); 
       _logger.debug("# Loading token swf with context from [{0}].", url); 
       _loader.load(swfUrl, loaderContext); 
   } 
   
   private function modEventHandler(e:Event):void { 
       _logger.debug("loadSWF with domainID {0}",  
       SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
           loader.contentLoaderInfo.applicationDomain. 
           getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray = myTokens. 
           FetchToken(SecurityDomain.currentDomain.domainID); 
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           _logger.debug("token bytearry size {0}", byteArray.length); 
           _authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   ```

   **Beispiel 2 mit mehreren Token:**

   ```
   private function tokenSwfLoadedHandler(e:Event):void { 
       trace("loadSWF with domainID {0}", SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
         loader.contentLoaderInfo.applicationDomain. 
         getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray =  
           myTokens.FetchToken(SecurityDomain.currentDomain.domainID); 
       var myDomains:Array = ["domain.com"]; 
       if (byteArray == null || byteArray.length == 0) { 
           // check for wildcard tokens 
           if (myTokens.hasOwnProperty("FetchWildCardToken") == true) { 
               // contains wildcard domains 
               for each (var domain:String in myDomains) { 
                   byteArray = myTokens.FetchWildCardToken(domain); 
                   if (byteArray != null && byteArray.length != 0) { 
                       break; 
                   } 
               }; 
           } 
       } 
   
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           trace("token bytearry size {0}", byteArray.length); 
           authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   
   private function loadDirectTokenURL():void { 
       trace("#onApplicationComplete Loading token from [{0}].", tokenUrl); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       authorizedFeatureHelper.loadFrom(tokenUrl); 
   }
   ```

