---
title: Bereitstellen von Inhalten
description: Bereitstellen von Inhalten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Bereitstellen von Inhalten {#delivering-content}

Primetime DRM ist unabhängig vom Versand-Mechanismus des Inhalts, da die Laufzeitumgebung die Netzwerkschicht abstrahiert und die geschützten Inhalte einfach dem Primetime DRM-Subsystem zur Verfügung stellt. Daher können Inhalte über HTTP, HTTP Dynamic Streaming, RTMP, RTMPE, HLS usw. bereitgestellt werden.

Abhängig vom Protokoll kann es jedoch zu komplizierten Eingriffen beim Abrufen der Metadaten des geschützten Inhalts kommen ( `DRMContentData` - normalerweise in Form einer sid geladenen [!DNL .metadata]-Datei). Diese DRM-Metadaten sind erforderlich, um eine beliebige `DRMManager`-API aufzurufen, wie z. B. das Vorabrufen der Lizenz, die DRM-Authentifizierung oder das Verbinden einer Gerätedomäne. Beispielsweise können mit dem RTMP/RTMPE-Protokoll nur FLV- und F4V-Daten über den Flash Media Server (FMS) an den Client gesendet werden. Aus diesem Grund muss der Client den Metadatenblock auf andere Weise abrufen. Eine Option zur Lösung dieses Problems besteht darin, die Metadaten auf einem HTTP-Webserver zu hosten und den Client-Videoplayer zu implementieren, um die entsprechenden Metadaten abzurufen, je nachdem, welcher Inhalt wiedergegeben wird.

```
private function getMetadata():void { 
    extrapolated-path-to-metadata = "https://metadatas.mywebserver.com/" + videoname; 
     var urlRequest : URLRequest =  
      new URLRequest(extrapolated-path-to-the-metadata + ".metadata");  
    var urlStream : URLStream = new URLStream();  
    urlStream.addEventListener(Event.COMPLETE, handleMetadata);  
    urlStream.addEventListener(IOErrorEvent.NETWORK_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.IO_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.VERIFY_ERROR, handleIOError);  
 
    try { 
        urlStream.load(urlRequest);  
    } catch(se:SecurityError) { 
        videoLog.text += se.toString() + "\n";  
    } catch(e:Error) { 
        videoLog.text += e.toString() + "\n";  
    } 
} 
```

