---
description: Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.
title: MediaPlayer einrichten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} einrichten

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.

1. `MediaPlayer` instanziieren und ein `android.content.Context`-Objekt an den Konstruktor übergeben:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geben Sie ein Rahmenlayout ( `android.widget.FrameLayout`) ein, um `ViewGroup` von `mediaPlayer` zu halten:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   Nachfolgend finden Sie das Codefragment zum Erstellen von `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Fügen Sie eine Ansicht von `mediaPlayer` in das Rahmenlayout ein:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>Die `MediaPlayer`-Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.