---
description: TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.
title: Media Player einrichten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Media Player einrichten {#set-up-the-media-player}

TVSDK bietet Tools zum Erstellen einer erweiterten Videoplayer-Anwendung (Ihr Primetime-Player), die Sie in andere Primetime-Komponenten integrieren können. Es bietet außerdem eine Reihe von Funktionen, mit denen die Qualität der Videowiedergabe maximiert werden kann.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instanziieren eines `MediaPlayer` und platzieren Sie eine Ansicht davon in einem Rahmen-Layout.

1. Instanziieren `MediaPlayer`, Übergeben einer `android.content.Context` -Objekt an den Konstruktor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Erstellen Sie ein Rahmenlayout ( `android.widget.FrameLayout`), um eine `ViewGroup` von `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Nachstehend finden Sie das zu erstellende Codefragment `_viewGroup`.

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

   >[!NOTE]
   >
   >Die `MediaPlayer` Instanz ( `mediaPlayer`) ist jetzt verfügbar und ordnungsgemäß konfiguriert, um Videoinhalte auf dem Gerätebildschirm anzuzeigen.
