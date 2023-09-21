---
description: Die MediaPlayer-Oberfläche für Android enthält die Funktionalität und das Verhalten eines Medienplayers.
title: MediaPlayer einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# MediaPlayer einrichten {#set-up-the-mediaplayer}

Die MediaPlayer-Oberfläche für Android enthält die Funktionalität und das Verhalten eines Medienplayers.

TVSDK bietet eine Implementierung der `MediaPlayer` -Schnittstelle, die `DefaultMediaPlayer` -Klasse. Wenn Sie eine Videowiedergabefunktion benötigen, instanziieren Sie `DefaultMediaPlayer`.

>[!TIP]
>
>Interagieren Sie mit dem `DefaultMediaPlayer` nur mit den Methoden, die von der `MediaPlayer` -Schnittstelle.

1. Instanziieren eines MediaPlayers mithilfe des öffentlichen `DefaultMediaPlayer.create` -Factory-Methode verwenden, wobei ein Java Android-Anwendungskontextobjekt übergeben wird.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Aufruf `MediaPlayer.getView` , um einen Verweis auf die `MediaPlayerView` -Instanz.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Platzieren Sie die `MediaPlayerView` -Instanz in einer `FrameLayout` -Instanz, die das Video auf dem Bildschirm des Geräts platziert.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

Die `MediaPlayer` -Instanz ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
