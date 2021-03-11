---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
title: Umleitungsoptimierung für 302 deaktivieren oder aktivieren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---


# HTTP 302 Umleitungsoptimierung {#http-302-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.

Wenn eine Hauptmanifestanforderung umgeleitet wird und die 302-Optimierung im Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch weitere 302 Antworten vermieden werden.

Diese Funktion ist standardmäßig aktiviert. Sie können diese Einstellung ändern.

## Umleitungsoptimierung für 302 deaktivieren oder aktivieren{#disable-or-enable-redirect-optimization}

Verwenden Sie die Eigenschaft `useRedirectedUrl`, um die 302-Umleitung zu aktivieren (true) oder zu deaktivieren (false).
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

