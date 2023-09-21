---
description: Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.
title: MediaPlayer einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# MediaPlayer einrichten {#set-up-the-mediaplayer}

TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

Instanziieren Sie einen MediaPlayer und platzieren Sie eine Ansicht davon in einem Frame-Layout.

1. Instanziieren `MediaPlayer`, Übergeben einer `android.content.Context` -Objekt an den Konstruktor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Erstellen Sie ein Rahmenlayout ( `android.widget.FrameLayout`), um eine `ViewGroup` von `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   Nachstehend finden Sie das zu erstellende Codefragment `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Platzieren einer Ansicht von `mediaPlayer` innerhalb des Rahmenlayouts:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>Die `MediaPlayer` Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
