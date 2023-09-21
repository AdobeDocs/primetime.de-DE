---
description: Das Flash Runtime TVSDK benötigt ein signiertes Token, um zu überprüfen, ob Sie berechtigt sind, die TVSDK-API in der Domäne aufzurufen, in der sich Ihre Anwendung befindet.
title: Signiertes Token laden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Signiertes Token laden {#load-your-signed-token}

Das Flash Runtime TVSDK benötigt ein signiertes Token, um zu überprüfen, ob Sie berechtigt sind, die TVSDK-API in der Domäne aufzurufen, in der sich Ihre Anwendung befindet.

1. Rufen Sie für jede Ihrer Domänen ein signiertes Token von Ihrem Adobe-Support-Mitarbeiter ab (wobei jede Domäne eine bestimmte Domäne oder eine Wildcard-Domäne sein kann).

       Um ein Token zu erhalten, geben Sie Adobe entweder die Domäne an, in der Ihre Anwendung gespeichert oder geladen wird, oder vorzugsweise die Domäne als SHA256-Hash. Im Gegenzug stellt Adobe ein signiertes Token für jede Domäne bereit. Diese Token haben eine der folgenden Formen:
   
   * Ein [!DNL .xml] -Datei, die als Token für eine einzelne Domäne oder Wildcard-Domäne fungiert.

     >[!NOTE]
     >
     >Ein Token für eine Wildcard-Domäne deckt diese Domäne und alle zugehörigen Subdomänen ab. Beispiel: ein Platzhalter-Token für die Domäne [!DNL mycompany.com] würde auch [!DNL vids.mycompany.com] und [!DNL private.vids.mycompany.com]; ein Platzhalter-Token für [!DNL vids.mycompany.com] würde auch [!DNL private.vids.mycompany.com]. *Wildcard-Domänen-Token werden nur für bestimmte Flash Player-Versionen unterstützt.*

   * A [!DNL .swf] -Datei mit Token-Informationen für mehrere Domänen (ohne Platzhalter) (einzeln oder als Platzhalter), die Ihre Anwendung dynamisch laden kann.

1. Speichern Sie die Token-Datei am selben Speicherort oder in der Domäne wie Ihre Anwendung.

   Standardmäßig sucht TVSDK an dieser Stelle nach dem Token. Alternativ können Sie den Namen und Speicherort des Tokens unter `flash_vars` in Ihrer HTML-Datei.
1. Wenn Ihre Token-Datei eine einzelne XML-Datei ist:
   1. Verwendung `utils.AuthorizedFeaturesHelper.loadFrom` , um die unter der angegebenen URL gespeicherten Daten (die Token-Datei) herunterzuladen und die `authorizedFeatures` Informationen.

      Dieser Schritt kann variieren. Sie können beispielsweise eine Authentifizierung durchführen, bevor Sie die Anwendung starten, oder das Token direkt von Ihrem Content Management System (CMS) empfangen.

   1. TVSDK sendet eine `COMPLETED` -Ereignis, wenn das Laden erfolgreich war, oder ein `FAILED` ansonsten. Führen Sie geeignete Maßnahmen durch, wenn Sie eines der beiden Ereignisse erkennen.

      Dies muss erfolgreich sein, damit Ihre Anwendung die erforderlichen `authorizedFeatures` Objekte in Form eines `MediaPlayerContext`.

   Dieses Beispiel zeigt, wie Sie ein einzelnes Token verwenden können [!DNL .xml] -Datei.

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

1. Wenn Ihr Token ein [!DNL .swf] Datei:
   1. Definieren Sie eine `Loader` -Klasse, um die [!DNL .swf] -Datei.
   1. Legen Sie die `LoaderContext` , um das Laden anzugeben, das in der aktuellen Anwendungsdomäne enthalten sein soll, wodurch TVSDK das richtige Token innerhalb der [!DNL .swf] -Datei. Wenn `LoaderContext` nicht angegeben ist, wird die Standardaktion von `Loader.load` ist es, die .swf-Datei in die untergeordnete Domäne der aktuellen Domäne zu laden.
   1. Suchen Sie nach dem COMPLETE-Ereignis, das von TVSDK ausgelöst wird, wenn das Laden erfolgreich ist.

      Suchen Sie auch nach dem ERROR-Ereignis und ergreifen Sie geeignete Maßnahmen.
   1. Wenn das Laden erfolgreich ist, verwenden Sie die `AuthorizedFeaturesHelper` um eine `ByteArray` enthält die PCKS-7-kodierten Sicherheitsdaten.

      Diese Daten werden über die AVE V11-API verwendet, um eine Autorisierungsbestätigung vom Flash Runtime Player zu erhalten. Wenn das Byte-Array keinen Inhalt hat, verwenden Sie stattdessen das Verfahren, um nach einer Token-Datei mit einer Domäne zu suchen.
   1. Verwendung `AuthorizedFeatureHelper.loadFeatureFromData` , um die erforderlichen Daten aus dem Byte-Array abzurufen.
   1. Entladen Sie die [!DNL .swf] -Datei.

   Die folgenden Beispiele zeigen, wie Sie ein Multitoken verwenden können [!DNL .swf] -Datei.

   **Beispiel 1 für ein Multitoken:**

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

   **Beispiel 2 für ein Multitoken:**

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
