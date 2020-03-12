---
description: Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.
seo-description: Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.
seo-title: MediaPlayer einrichten
title: MediaPlayer einrichten
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayer einrichten {#set-up-the-mediaplayer}

Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.

TVSDK bietet eine Implementierung der `MediaPlayer` Schnittstelle, die `DefaultMediaPlayer` Klasse. Wenn Sie eine Videowiedergabefunktion benötigen, instanziieren Sie `DefaultMediaPlayer`.

>[!TIP]
>
>Interagieren Sie mit der `DefaultMediaPlayer` Instanz nur mit den Methoden, die von der `MediaPlayer` Schnittstelle bereitgestellt werden.

1. Instanziieren Sie einen MediaPlayer mithilfe der öffentlichen `DefaultMediaPlayer.create` Factory-Methode, wobei Sie ein Java-Android-Anwendungskontextobjekt übergeben.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Aufruf `MediaPlayer.getView` zum Abrufen eines Verweises auf die `MediaPlayerView` Instanz.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Platzieren Sie die `MediaPlayerView` Instanz in einer `FrameLayout` Instanz, in der das Video auf dem Bildschirm des Geräts angezeigt wird.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

Die `MediaPlayer` Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
