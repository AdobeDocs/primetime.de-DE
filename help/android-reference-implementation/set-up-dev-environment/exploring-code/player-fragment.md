---
description: In der PlayerFragment-Klasse bearbeiten Sie den Code, um die voll aktivierten Feature Manager zu erstellen.
title: PlayerFragment
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# PlayerFragment {#playerfragment}

In der PlayerFragment-Klasse bearbeiten Sie den Code, um die voll aktivierten Feature Manager zu erstellen.

Die `PlayerFragment`-Klasse enthält alle Komponenten der Benutzeroberfläche, wie `playerFrame`, `ControlBar`, `playerClickableAdFragment` und `adOverlay`.

Es verarbeitet die Initialisierung all dieser Komponenten sowie das Erstellen des Players, Einrichten der Ansichten, Erstellen von Feature-Managern für den Medienplayer, Bearbeiten von Media-Ereignissen wie Fortsetzen, Abspielen, Anhalten und Bearbeiten der Ereignis-Listener für `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager` und `EntitlementManager`.

Die XML-Datei, die die Konfigurationsparameter für `PlayerFragment` enthält, ist `res/layout/fragment_player.xml`.

Bevor Sie die Funktionsmanager erstellen, müssen Sie den Medienplayer erstellen, indem Sie sicherstellen, dass der folgende Code in der Datei `PlayerFragment.java` enthalten ist:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
