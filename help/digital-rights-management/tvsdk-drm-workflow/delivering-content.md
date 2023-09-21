---
title: Inhalt bereitstellen
description: Inhalt bereitstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Inhalt bereitstellen {#delivering-content}

Primetime DRM ist unabhängig vom Bereitstellungsmechanismus des Inhalts, da die Laufzeitumgebung die Netzwerkschicht abstrahiert und dem Primetime-DRM-Subsystem einfach den geschützten Inhalt bereitstellt. Daher können Inhalte über HTTP, HTTP Dynamic Streaming, RTMP, RTMPE, HLS usw. bereitgestellt werden.

Abhängig vom Protokoll können jedoch auch die Metadaten des geschützten Inhalts ( `DRMContentData` - in der Regel in Form einer Seitenladung [!DNL .metadata] -Datei). Diese DRM-Metadaten sind erforderlich, um alle `DRMManager` API, z. B. Vorabruf der Lizenz, DRM-Authentifizierung oder Beitritt zu einer Gerätedomäne. Beispielsweise können mit dem RTMP/RTMPE-Protokoll nur FLV- und F4V-Daten über den Flash Media Server (FMS) an den Client gesendet werden. Aus diesem Grund muss der Client den Metadatenblock auf andere Weise abrufen. Eine Option zur Lösung dieses Problems besteht darin, die Metadaten auf einem HTTP-Webserver zu hosten und den Client-Videoplayer zu implementieren, um die entsprechenden Metadaten abzurufen, je nach wiedergegebenen Inhalten.

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
