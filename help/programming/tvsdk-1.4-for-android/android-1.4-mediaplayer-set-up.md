---
description: Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.
seo-description: Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.
seo-title: MediaPlayer einrichten
title: MediaPlayer einrichten
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} einrichten

Die MediaPlayer-Schnittstelle für Android enthält die Funktionen und das Verhalten eines Medienplayers.

TVSDK stellt eine Implementierung der `MediaPlayer`-Schnittstelle bereit, die `DefaultMediaPlayer`-Klasse. Wenn Sie eine Funktion für die Videowiedergabe benötigen, instanziieren Sie `DefaultMediaPlayer`.

>[!TIP]
>
>Interagieren Sie mit der `DefaultMediaPlayer`-Instanz nur mit den Methoden, die von der `MediaPlayer`-Schnittstelle bereitgestellt werden.

1. Instanziieren Sie einen MediaPlayer mit der Factory-Methode public `DefaultMediaPlayer.create`, wobei Sie ein Java Android-Anwendungskontextobjekt übergeben.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Rufen Sie `MediaPlayer.getView` auf, um einen Verweis auf die `MediaPlayerView`-Instanz abzurufen.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Platzieren Sie die `MediaPlayerView`-Instanz in einer `FrameLayout`-Instanz, in der das Video auf dem Bildschirm des Geräts abgelegt wird.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

Die `MediaPlayer`-Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
