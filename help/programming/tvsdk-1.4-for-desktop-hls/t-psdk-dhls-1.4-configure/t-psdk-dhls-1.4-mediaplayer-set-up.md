---
description: Die MediaPlayer-Oberfläche kapselt die Funktionalität und das Verhalten eines Medienplayers.
title: MediaPlayer einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# MediaPlayer einrichten {#set-up-the-mediaplayer}

TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Medienplayer-Ansicht in TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. TVSDK bietet beispielsweise Methoden zum Abspielen und Anhalten. Sie können Schaltflächen für die Benutzeroberfläche auf Ihrer Plattform erstellen und die Schaltflächen festlegen, um diese TVSDK-Methoden aufzurufen. Die MediaPlayer-Oberfläche enthält die Funktionen und das Verhalten eines Medienplayers.

TVSDK bietet eine einzige Implementierung der `MediaPlayer` -Schnittstelle: die DefaultMediaPlayer-Klasse. Wenn Sie eine Funktion für die Videowiedergabe benötigen, instanziieren Sie `DefaultMediaPlayer`.

>[!NOTE]
>
>Interagieren Sie mit dem `DefaultMediaPlayer` nur mit den Methoden, die von der `MediaPlayer` -Schnittstelle.

1. Instanziieren eines `MediaPlayerContext` mit der Anwendung geladen `authorizedFeatures` -Instanz (siehe [Signiertes Token laden](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instanziieren eines `MediaPlayer` mithilfe der öffentlichen Factory-Methode erstellen, übergeben Sie eine `MediaPlayerContext` context -Objekt:

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Dadurch wird eine generische `MediaPlayer` -Schnittstelle. 1. Instanziieren eines `MediaPlayerView` und geben Sie die zu verwendende StageVideo-Instanz an:

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Verknüpfen Sie die `MediaPlayerView` -Instanz mit der neu erstellten Ansicht:

   ```
   mediaPlayer.view = view;
   ```

1. Platzieren Sie die `MediaPlayerView` -Instanz auf dem Bildschirm des Geräts:

   ```
   container.addChild(view)
   ```

Die `MediaPlayer` -Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
