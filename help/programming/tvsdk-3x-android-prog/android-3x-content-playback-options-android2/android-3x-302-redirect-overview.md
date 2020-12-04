---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
seo-description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
seo-title: HTTP 302 Umleitungsoptimierung
title: HTTP 302 Umleitungsoptimierung
uuid: 91ed8919-a3c1-4e57-9eaf-e3ba430de35f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 1%

---


# HTTP 302 Umleitungsoptimierung {#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.

Wenn eine Hauptmanifestanforderung umgeleitet wird und die 302-Optimierung im Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch weitere 302 Antworten vermieden werden. Diese Funktion ist standardmäßig aktiviert. Sie können diese Einstellung ändern.

## 302-Umleitungsoptimierung {#section_8977448B268E41D69A8F75B60EB9DA3B} deaktivieren oder aktivieren

Verwenden Sie die Eigenschaft `useRedirectedUrl`, um die 302-Umleitung zu aktivieren ( `true`) oder zu deaktivieren ( `false`).

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
