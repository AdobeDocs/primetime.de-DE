---
description: Browser TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.
title: Flash Failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Flash Failover {#flash-failover}

Browser TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Medienplayer-Ansicht im Browser TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. Beispiel: Browser TVSDK bietet Methoden zum Abspielen und Anhalten. Sie können Schaltflächen für die Benutzeroberfläche auf Ihrer Plattform erstellen und die Schaltflächen festlegen, um diese Browser TVSDK-Methoden aufzurufen.

## Flash Fallback {#section_92D3884A13A6431F9A9CC5C79715D888}

Im Browser TVSDK interagiert Ihre Anwendung nur mit dem `Primetime.js` API. Die zugrunde liegende TVSDK-Implementierung des Browsers bestimmt anhand der aktuellen Plattform und des Ressourcentyps der abzuspielenden Medien, welche Player-Technologie verwendet werden soll.

Die Entscheidung für die Player-Technologie wird erst getroffen, wenn Sie `MediaPlayer.replaceCurrentResource` , um eine bestimmte Ressource wiederzugeben.

Beispiel:

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## Bestimmen des zu verwendenden Medienplayers {#section_D844E386AF5848688D204DEE258ECEE6}

Dieses Beispielverfahren veranschaulicht den Prozess zur Bestimmung der Player-Technologie:

>[!TIP]
>
>Der Prozess kann je nach URL und Umgebung variieren.

1. Wenn Media Source-Erweiterungen unterstützt werden, verwenden Sie sie ohne bekannte Einschränkungen.
1. Wenn unterstützt, verwenden Sie die `<video>` -Tag direkt ohne MSE.
1. Stellen Sie sicher, dass Sie mindestens Adobe Flash Player Version 23.0 verwenden.
1. Wenn keine geeignete Wiedergabetechnologie gefunden wird, `replaceCurrentResource` gibt einen Fehler zurück.

Eine nachfolgende `replaceCurrentResource` Aufruf für denselben `MediaPlayer` -Instanz folgt demselben Prozess. Auf diese Weise können Sie verschiedene Ressourcentypen mit dem gleichen `MediaPlayer` -Instanz im selben übergeordneten Element `<DIV>` -Tag, das Sie beim `MediaPlayerView` -Instanz erstellt wurde.

>[!TIP]
>
>Das SWF-Objekt und die `<video>` -Tag im übergeordneten `<DIV>` -Tag.
