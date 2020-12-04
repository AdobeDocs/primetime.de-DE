---
description: Browser TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.
seo-description: Browser TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.
seo-title: 'null'
title: 'null'
uuid: 57b35a5f-87f8-41a2-ad85-300b999dc30b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Flash-Failover {#flash-failover}

Browser TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Media Player-Ansicht in Browser TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. Browser TVSDK bietet beispielsweise Methoden zum Abspielen und Anhalten. Sie können auf Ihrer Plattform Schaltflächen für die Benutzeroberfläche erstellen und die Schaltflächen einstellen, um diese Browser TVSDK-Methoden aufzurufen.

## Flash-Fallback {#section_92D3884A13A6431F9A9CC5C79715D888}

In Browser TVSDK interagiert Ihre Anwendung nur mit der API `Primetime.js`. Die zugrunde liegende Browser TVSDK-Implementierung entscheidet, welche Player-Technologie basierend auf der aktuellen Plattform und dem Ressourcentyp des Mediums, das abgespielt werden soll, verwendet werden soll.

Die Entscheidung für die Player-Technologie wird erst getroffen, wenn Sie `MediaPlayer.replaceCurrentResource` aufrufen, um eine bestimmte Ressource abzuspielen.

Beispiel:

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## Legen Sie den Medienplayer fest, der {#section_D844E386AF5848688D204DEE258ECEE6} verwenden soll.

Dieses Beispielverfahren veranschaulicht den Prozess der Bestimmung der Player-Technologie:

>[!TIP]
>
>Der Vorgang kann je nach URL und Umgebung variieren.

1. Wenn Media Source-Erweiterungen unterstützt werden, verwenden Sie sie ohne bekannte Einschränkungen.
1. Falls unterstützt, verwenden Sie das `<video>`-Tag direkt ohne MSE.
1. Stellen Sie sicher, dass Sie mindestens Adobe Flash Player Version 23.0 verwenden.
1. Wenn keine geeignete Wiedergabetechnologie gefunden wird, gibt `replaceCurrentResource` einen Fehler zurück.

Ein nachfolgender `replaceCurrentResource`-Aufruf für dieselbe `MediaPlayer`-Instanz folgt demselben Vorgang. Auf diese Weise können Sie verschiedene Ressourcentypen wiedergeben, indem Sie dieselbe `MediaPlayer`-Instanz im selben übergeordneten `<DIV>`-Tag verwenden, das Sie beim Erstellen der `MediaPlayerView`-Instanz angegeben haben.

>[!TIP]
>
>Das SWF-Objekt und das `<video>`-Tag sind im übergeordneten `<DIV>`-Tag verschachtelt.

