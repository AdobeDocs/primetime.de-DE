---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
title: HTTP 302 Umleitungsoptimierung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---


# HTTP 302 Umleitungsoptimierung{#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.

Wenn eine Hauptmanifestanforderung umgeleitet wird und die 302-Optimierung im Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch weitere 302 Antworten vermieden werden.

Diese Funktion ist standardmäßig deaktiviert. Sie können diese Einstellung ändern.

Wenn Sie diese Funktion aktivieren, funktioniert sie nur dann fehlerfrei, wenn *alle* der folgenden Bedingungen wahr sind: Andernfalls findet keine Umleitungsoptimierung statt, und es werden weiterhin 302 Antworten angezeigt:

* Ihre Anwendung wurde für Adobe Flash Player 11.8 mit `-swf-version` 21 oder höher kompiliert.
* Ihre Endbenutzer haben Adobe Flash Player 11.8 oder höher installiert.

>[!IMPORTANT]
>
>Um sicherzustellen, dass Cookies mit Anzeigenanforderungen übergeben werden, deaktivieren Sie die 302-Umleitung. Wenn 302-Umleitungen aktiviert sind, wird die Anzeigenanforderung möglicherweise in eine Domäne umgeleitet, die sich von der Domäne unterscheidet, von der das Cookie stammt.

## 302-Umleitungsoptimierung {#section_D6687FC44C61446F878008B629A5FA19} deaktivieren oder aktivieren

Verwenden Sie die Eigenschaft `useRedirectedUrl`, um die 302-Umleitung zu aktivieren (true) oder zu deaktivieren (false).

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

