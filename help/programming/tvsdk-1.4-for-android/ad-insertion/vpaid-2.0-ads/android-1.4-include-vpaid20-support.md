---
description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
seo-title: Implementierung der VPAID 2.0-Integration
title: Implementierung der VPAID 2.0-Integration
uuid: 7d11ffd8-240c-4a95-94e6-ff4417c8942e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---


# Implementierung der VPAID 2.0-Integration{#implement-vpaid-integration}

Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.

So fügen Sie VPAID 2.0-Unterstützung hinzu:

1. hinzufügen der benutzerdefinierten Anzeigen-Ansicht auf die Player-Oberfläche.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. hinzufügen eines Listeners für benutzerdefinierte Anzeigen-Ereignis.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

