---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.
title: 302-Umleitungsoptimierung deaktivieren oder aktivieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# HTTP 302-Umleitungsoptimierung {#http-302-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.

Wenn eine Hauptmanifest-Anforderung umgeleitet wird und die Optimierung von 302 in Ihrem Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch zusätzliche 302 Antworten vermieden werden.

Diese Funktion ist standardmäßig aktiviert und Sie können diese Einstellung ändern.

## 302-Umleitungsoptimierung deaktivieren oder aktivieren{#disable-or-enable-redirect-optimization}

Verwenden Sie die `useRedirectedUrl` -Eigenschaft zum Aktivieren (true) oder Deaktivieren (false) der 302-Umleitung.
Beispiel:

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration as Metadata: 
MetadataNode resourceMetadata = new MetadataNode();  
resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                         networkConfiguration); 
 
//Call MediaResource.createFromURL to set the metadata: 
MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
  
//Load the resource 
mediaPlayer.replaceCurrentItem(resource);
```
