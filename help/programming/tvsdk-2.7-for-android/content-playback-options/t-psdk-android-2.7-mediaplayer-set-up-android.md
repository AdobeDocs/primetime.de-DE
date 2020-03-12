---
description: Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.
seo-description: Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.
seo-title: MediaPlayer einrichten
title: MediaPlayer einrichten
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# MediaPlayer einrichten {#set-up-the-mediaplayer}

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.

1. Instanziieren `MediaPlayer`und Übergeben eines `android.content.Context` Objekts an den Konstruktor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geben Sie ein Rahmenlayout ( `android.widget.FrameLayout`) an, um eine `ViewGroup` der folgenden Optionen einzuhalten `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   Unten sehen Sie das zu erstellende Codefragment `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Platzieren Sie eine Ansicht von `mediaPlayer` innerhalb des Rahmenlayouts:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>Die `MediaPlayer` Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.