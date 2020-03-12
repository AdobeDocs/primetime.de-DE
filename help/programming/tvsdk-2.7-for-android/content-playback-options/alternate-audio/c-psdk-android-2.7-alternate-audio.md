---
description: Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für eine Videospur wechseln. Benutzer können bei der Wiedergabe des Videos die gewünschte Sprachspur auswählen.
seo-description: Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für eine Videospur wechseln. Benutzer können bei der Wiedergabe des Videos die gewünschte Sprachspur auswählen.
seo-title: Alternativaudio
title: Alternativaudio
uuid: 86aa5393-6a9e-49db-807b-7299e6b4ab2b
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Übersicht {#alternate-audio-overview}

Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für eine Videospur wechseln. Benutzer können bei der Wiedergabe des Videos die gewünschte Sprachspur auswählen.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wenn TVSDK die `MediaPlayerItem` Instanz für das aktuelle Video erstellt, wird für jede verfügbare Audiospur ein `AudioTrack` Element erstellt. Das Element enthält eine `name` Eigenschaft, bei der es sich um eine Zeichenfolge handelt, die in der Regel eine vom Benutzer erkennbare Beschreibung der Sprache dieser Spur enthält. Das Element enthält auch Informationen darüber, ob diese Verfolgung standardmäßig verwendet werden soll. Wenn es Zeit ist, das Video abzuspielen, können Sie nach einer Liste der verfügbaren Audiospuren fragen, optional zulassen, dass der Benutzer eine Spur auswählt und das Video mit der ausgewählten Spur abspielt.

>[!TIP]
>
>Obwohl selten, wenn eine zusätzliche Audiospur verfügbar wird, nachdem TVSDK die `MediaPlayerItem`, TVSDK löst ein `MediaPlayerItem.AUDIO_TRACK_UPDATED` Ereignis aus.

## APIs hinzugefügt {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Die folgenden APIs wurden hinzugefügt, um alternative Audio zu unterstützen:

`hasAlternateAudio`

Wenn das angegebene Medium über eine andere Audiospur als die Standardspur verfügt, gibt diese boolesche Funktion zurück `true`. Wenn keine alternative Audiospur vorhanden ist, gibt die Funktion zurück `false`.

```java
boolean hasAlternateAudio();
```

** `getAudioTracks`**

Diese Funktion gibt die Liste aller aktuell verfügbaren Audiospuren in einem angegebenen Medium zurück.

```java
List<AudioTrack> getAudioTracks();
```

`getSelectedAudioTrack`

Diese Funktion gibt die derzeit ausgewählte alternative Audiospur und Eigenschaften wie Sprache zurück. Die automatische Auswahl der Spur kann ebenfalls extrahiert werden.

```java
AudioTrack getSelectedAudioTrack();
```

`selectAudioTrack`

Diese Funktion wählt eine alternative Audiospur für die Wiedergabe aus.

```java
void selectAudioTrack(AudioTrack audioTrack);
```

Beispiel:

```java
private void onPrepared() { 
    // Select the AA track in PREPARED State 
    boolean hasAlternateAudio = _mediaPlayer.getCurrentItem().hasAlternateAudio(); 
    if(hasAlternateAudio) { 
        AudioTrack selectedAudioTrack =  
          _mediaPlayer.getCurrentItem().getSelectedAudioTrack(); 
 
        if (selectedAudioTrack == null) {  
            // Selecting default audio track  
            // If index is 1 it will select alternate audio track  
            selectedAudioTrack = _mediaPlayer.getCurrentItem().getAudioTracks().get(0);  
        } 
    } 
    _mediaPlayer.getCurrentItem().selectAudioTrack(selectedAudioTrack); 
} 
```

