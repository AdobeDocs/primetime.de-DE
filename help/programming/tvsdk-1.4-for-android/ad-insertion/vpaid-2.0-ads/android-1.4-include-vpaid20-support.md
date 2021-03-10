---
description: Um VPAID 2.0-Unterstützung hinzuzufügen, fügen Sie eine benutzerdefinierte Anzeigenbenutzerspezifische Ansicht und entsprechende Listener hinzu.
title: Implementierung der VPAID 2.0-Integration
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
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

