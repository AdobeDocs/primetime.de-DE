---
description: In der PlayerFragment-Klasse bearbeiten Sie den Code, um die voll aktivierten Feature Manager zu erstellen.
seo-description: In der PlayerFragment-Klasse bearbeiten Sie den Code, um die voll aktivierten Feature Manager zu erstellen.
seo-title: PlayerFragment
title: PlayerFragment
uuid: 83f02c31-f3b1-4d16-97c8-5b391e8c999a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# PlayerFragment {#playerfragment}

In der PlayerFragment-Klasse bearbeiten Sie den Code, um die voll aktivierten Feature Manager zu erstellen.

Die `PlayerFragment` Klasse enthält alle UI-Komponenten wie `playerFrame`, `ControlBar`, `playerClickableAdFragment`und `adOverlay`.

Es verwaltet die Initialisierung all dieser Komponenten sowie das Erstellen des Players, Einrichten der Ansichten, Erstellen von Feature-Managern für den Medienplayer, Bearbeiten von Media-Ereignissen wie Fortsetzen, Abspielen, Anhalten und Bearbeiten der Ereignis-Listener für `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`und `EntitlementManager`.

Die XML-Datei mit den Konfigurationsparametern für die `PlayerFragment` ist `res/layout/fragment_player.xml`.

Bevor Sie die Feature Manager erstellen, müssen Sie den Medienplayer erstellen, indem Sie sicherstellen, dass der folgende Code in der `PlayerFragment.java` Datei enthalten ist:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
