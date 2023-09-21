---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.
title: HTTP 302-Umleitungsoptimierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# HTTP 302-Umleitungsoptimierung {#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitantworten, was es Ihrer Anwendung ermöglicht, den Lastenausgleich effektiver zu gestalten.

Wenn eine Hauptmanifest-Anforderung umgeleitet wird und die Optimierung von 302 in Ihrem Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch zusätzliche 302 Antworten vermieden werden. Diese Funktion ist standardmäßig aktiviert und Sie können diese Einstellung ändern.

>[!IMPORTANT]
>
>Diese Funktion wird nur in zertifizierten Browsern unterstützt, die die `responseURL` -Eigenschaft in der `XMLHttpRequest` -Objekt.

Beachten Sie beim Flash-Fallback die folgenden Informationen:

* Ihre Endbenutzer müssen Adobe Flash Player Version 23 oder höher installiert haben.
* Wenn die Stream-Integrität deaktiviert ist, wird die 302-Weiterleitung nur bei zertifizierten Browsern unterstützt.

## Deaktivieren der Umleitungsoptimierung 302 {#disabling-redirect-optimization}

Sie können die useRedirectUrl -Eigenschaft verwenden, um die 302-Umleitung (true) oder die Deaktivierung (false) zu aktivieren.

Beispiel:

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
