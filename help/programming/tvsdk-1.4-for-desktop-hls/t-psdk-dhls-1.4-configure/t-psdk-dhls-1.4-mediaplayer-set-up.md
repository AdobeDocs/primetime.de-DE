---
description: Die MediaPlayer-Schnittstelle kapselt die Funktionen und das Verhalten eines Medienplayers.
seo-description: Die MediaPlayer-Schnittstelle kapselt die Funktionen und das Verhalten eines Medienplayers.
seo-title: MediaPlayer einrichten
title: MediaPlayer einrichten
uuid: 4b27643c-9ccd-4abb-9793-475d06ee2a88
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} einrichten

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können.

Verwenden Sie die Tools Ihrer Plattform, um einen Player zu erstellen und ihn mit der Media Player-Ansicht in TVSDK zu verbinden, die über Methoden zum Abspielen und Verwalten von Videos verfügt. TVSDK bietet beispielsweise Methoden zum Abspielen und Anhalten. Sie können auf Ihrer Plattform Schaltflächen für die Benutzeroberfläche erstellen und die Schaltflächen so einstellen, dass diese TVSDK-Methoden aufgerufen werden. Die MediaPlayer-Schnittstelle enthält die Funktionen und das Verhalten eines Medienplayers.

TVSDK bietet eine einzelne Implementierung der `MediaPlayer`-Schnittstelle: die DefaultMediaPlayer-Klasse. Wenn Sie eine Video-Wiedergabe-Funktion benötigen, instanziieren Sie `DefaultMediaPlayer`.

>[!NOTE]
>
>Interagieren Sie mit der `DefaultMediaPlayer`-Instanz nur mit den Methoden, die von der `MediaPlayer`-Schnittstelle bereitgestellt werden.

1. Instanziieren Sie eine `MediaPlayerContext`-Instanz, die von der Anwendung geladen wird (siehe [Ihr signiertes Token laden](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).`authorizedFeatures`

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instanziieren Sie ein `MediaPlayer` mit der öffentlichen Factory-Methode erstellen und übergeben Sie ein `MediaPlayerContext`-Kontextobjekt:

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Dadurch wird eine generische `MediaPlayer`-Schnittstelle zurückgegeben. 1. Instanziieren Sie ein `MediaPlayerView` und geben Sie die zu verwendende StageVideo-Instanz an:

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Verknüpfen Sie die `MediaPlayerView`-Instanz mit der neu erstellten Ansicht:

   ```
   mediaPlayer.view = view;
   ```

1. Platzieren Sie die `MediaPlayerView`-Instanz auf dem Bildschirm des Geräts:

   ```
   container.addChild(view)
   ```

Die `MediaPlayer`-Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.