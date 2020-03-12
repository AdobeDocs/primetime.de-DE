---
description: TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.
seo-description: TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.
seo-title: Media Player einrichten
title: Media Player einrichten
uuid: 1f672484-b340-4f92-8a47-dad4c9f3b3fc
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Media Player einrichten {#set-up-the-media-player}

TVSDK bietet Werkzeuge zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanziieren Sie eine `MediaPlayer` und platzieren Sie eine Ansicht davon in ein Rahmenlayout.

1. Instanziieren `MediaPlayer`und Übergeben eines `android.content.Context` Objekts an den Konstruktor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geben Sie ein Rahmenlayout ( `android.widget.FrameLayout`) an, um eine `ViewGroup` der folgenden Optionen einzuhalten `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Unten sehen Sie das zu erstellende Codefragment `_viewGroup`.

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

   >[!NOTE]
   >
   >Die `MediaPlayer` Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.