---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.
title: HTTP 302-Umleitungsoptimierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# HTTP 302-Umleitungsoptimierung{#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.

Wenn eine Hauptmanifest-Anforderung umgeleitet wird und die Optimierung von 302 in Ihrem Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch zusätzliche 302 Antworten vermieden werden.

Diese Funktion ist standardmäßig deaktiviert und Sie können diese Einstellung ändern.

Wenn Sie diese Funktion aktivieren, funktioniert sie nur dann ordnungsgemäß, wenn *all* die folgenden Bedingungen erfüllt sind; andernfalls findet keine Umleitungsoptimierung statt und es werden weiterhin 302 Antworten ausgegeben:

* Ihre Applikation wurde für Adobe Flash Player 11.8 kompiliert, unter Verwendung von `-swf-version` 21 oder höher.
* Ihre Endbenutzer haben Adobe Flash Player 11.8 oder höher installiert.

>[!IMPORTANT]
>
>Um sicherzustellen, dass Cookies mit Anzeigenanfragen übergeben werden, deaktivieren Sie die 302-Umleitung. Wenn die Umleitung auf 302 aktiviert ist, wird die Anzeigenanforderung möglicherweise an eine Domäne umgeleitet, die sich von der Domäne unterscheidet, von der das Cookie stammt.

## 302-Umleitungsoptimierung deaktivieren oder aktivieren {#section_D6687FC44C61446F878008B629A5FA19}

Verwenden Sie die `useRedirectedUrl` -Eigenschaft zum Aktivieren (true) oder Deaktivieren (false) der 302-Umleitung.

<!--<a id="example_B886777252B745AAB48B1FCC42C97A25"></a>-->

Beispiel:

```
// Set useRedirectedUrl property to true 
var networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = true; 
  
//Set NetworkConfiguration as Metadata: 
var result:Metadata = new Metadata(); 
result.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                   networkConfiguration); 
  
var mediaResource = new MediaResource( url, MediaResourceType.HLS, result); 
  
// load the resource 
mediaPlayer.replaceCurrentResource( mediaResource, mediaPlayerItemConfig );
```
