---
description: TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.
seo-description: TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.
seo-title: Media Player einrichten
title: Media Player einrichten
uuid: 1f672484-b340-4f92-8a47-dad4c9f3b3fc
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Medienplayer {#set-up-the-media-player} einrichten

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanziieren Sie ein `MediaPlayer` und platzieren Sie eine Ansicht davon in einem Rahmenlayout.

1. `MediaPlayer` instanziieren und ein `android.content.Context`-Objekt an den Konstruktor übergeben:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geben Sie ein Rahmenlayout ( `android.widget.FrameLayout`) ein, um `ViewGroup` von `mediaPlayer` zu halten:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Nachfolgend finden Sie das Codefragment zum Erstellen von `_viewGroup`.

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

   >[!NOTE]
   >
   >Die `MediaPlayer`-Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.