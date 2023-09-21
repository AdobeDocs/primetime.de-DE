---
description: In der PlayerFragment-Klasse bearbeiten Sie den Code, um die vollaktivierten Feature Manager zu erstellen.
title: PlayerFragment
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# PlayerFragment {#playerfragment}

In der PlayerFragment-Klasse bearbeiten Sie den Code, um die vollaktivierten Feature Manager zu erstellen.

Die `PlayerFragment` -Klasse enthält alle UI-Komponenten, z. B. die `playerFrame`, `ControlBar`, `playerClickableAdFragment`, und `adOverlay`.

Sie verarbeitet die Initialisierung all dieser Komponenten sowie die Erstellung des Players, die Einrichtung der Ansichten, die Erstellung von Feature Managern für den Medienplayer, die Verarbeitung von Medienereignissen wie Fortsetzen, Wiedergabe und Pause sowie die Verarbeitung der Ereignis-Listener für `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`, und `EntitlementManager`.

Die XML-Datei, die die Konfigurationsparameter für die `PlayerFragment` is `res/layout/fragment_player.xml`.

Bevor Sie die Feature Manager erstellen, müssen Sie den Media Player erstellen, indem Sie sicherstellen, dass der folgende Code im `PlayerFragment.java` Datei:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
