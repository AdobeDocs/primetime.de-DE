---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.
title: HTTP 302-Umleitungsoptimierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# HTTP 302-Umleitungsoptimierung {#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.

Wenn eine Hauptmanifest-Anforderung umgeleitet wird und die Optimierung von 302 in Ihrem Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch zusätzliche 302 Antworten vermieden werden. Diese Funktion ist standardmäßig aktiviert und Sie können diese Einstellung ändern.

## 302-Umleitungsoptimierung deaktivieren oder aktivieren {#section_8977448B268E41D69A8F75B60EB9DA3B}

Verwenden Sie die `useRedirectedUrl` -Eigenschaft zum Aktivieren der 302-Umleitung ( `true`) oder aus ( `false`).

<!--<a id="example_888749F70C8A43279D06A29BD68E7E4D"></a>-->

Beispiel:

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration on MediaPlayerItemConfig 
MediaPlayerItemConfig config = new MediaPlayerItemConfig (); 
config.setNetworkConfiguration(networkConfiguration); 
 
//Use this config when loading the MediaPlayerItem or calling replaceCurrentResource
```
