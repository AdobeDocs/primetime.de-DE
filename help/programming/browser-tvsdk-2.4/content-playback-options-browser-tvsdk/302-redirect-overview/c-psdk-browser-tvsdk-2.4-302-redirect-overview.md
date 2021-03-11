---
description: Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.
title: HTTP 302 Umleitungsoptimierung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---


# HTTP 302 Umleitungsoptimierung {#http-redirect-optimization}

Die 302-Umleitungsoptimierung minimiert die Anzahl der 302 Umleitungs-Antworten, wodurch Ihre Anwendung den Lastenausgleich effektiver gestalten kann.

Wenn eine Hauptmanifestanforderung umgeleitet wird und die 302-Optimierung im Player aktiviert ist, verwenden nachfolgende Anforderungen für Assets aus diesem Manifest den endgültigen Domänenspeicherort, wodurch weitere 302 Antworten vermieden werden. Diese Funktion ist standardmäßig aktiviert. Sie können diese Einstellung ändern.

>[!IMPORTANT]
>
>Diese Funktion wird nur in zertifizierten Browsern unterstützt, die die `responseURL`-Eigenschaft im `XMLHttpRequest`-Objekt unterstützen.

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
