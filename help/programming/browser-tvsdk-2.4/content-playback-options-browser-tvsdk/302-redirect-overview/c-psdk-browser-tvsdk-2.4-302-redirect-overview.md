---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
seo-description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
seo-title: HTTP 302 Umleitungsoptimierung
title: HTTP 302 Umleitungsoptimierung
uuid: d3009c6c-320a-4c0f-b6ba-bf6473049823
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# HTTP 302 Umleitungsoptimierung {#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.

Wenn eine Hauptmanifestanforderung umgeleitet wird und die 302-Optimierung im Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch weitere 302 Antworten vermieden werden. Diese Funktion ist standardmäßig aktiviert. Sie können diese Einstellung ändern.

>[!IMPORTANT]
>
>Diese Funktion wird nur in zertifizierten Browsern unterstützt, die die `responseURL` Eigenschaft im `XMLHttpRequest` Objekt unterstützen.

Beachten Sie für Flash-Fallback die folgenden Informationen:

* Endbenutzer müssen Adobe Flash Player Version 23 oder höher installiert haben.
* Wenn die Stream-Integrität deaktiviert ist, wird 302-Umleitungen nur in zertifizierten Browsern unterstützt.

## Deaktivieren der 302-Umleitungsoptimierung {#disabling-redirect-optimization}

Mit der useRedirectUrl-Eigenschaft können Sie 302-Umleitungen aktivieren (true) oder deaktivieren (false).

Beispiel:

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
