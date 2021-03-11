---
description: Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für eine Videospur wechseln. Benutzer können bei der Wiedergabe des Videos die gewünschte Sprachspur auswählen.
title: Alternativaudio
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# Übersicht {#alternate-audio-overview}

Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für eine Videospur wechseln. Benutzer können bei der Wiedergabe des Videos die gewünschte Sprachspur auswählen.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wenn TVSDK die `MediaPlayerItem`-Instanz für das aktuelle Video erstellt, wird für jede verfügbare Audiospur ein `AudioTrack`-Element erstellt. Das Element enthält eine `name`-Eigenschaft, bei der es sich um eine Zeichenfolge handelt, die in der Regel eine benutzererkennbare Beschreibung der Sprache dieser Spur enthält. Das Element enthält auch Informationen darüber, ob diese Verfolgung standardmäßig verwendet werden soll. Wenn es Zeit ist, das Video abzuspielen, können Sie nach einer Liste der verfügbaren Audiospuren fragen, optional zulassen, dass der Benutzer eine Spur auswählt und das Video mit der ausgewählten Spur abspielt.

>[!TIP]
>
>Obwohl dies selten der Fall ist, löst TVSDK ein `MediaPlayerItem.AUDIO_TRACK_UPDATED`-Ereignis aus, wenn eine zusätzliche Audiospur verfügbar ist, nachdem TVSDK das `MediaPlayerItem` erstellt hat.

## APIs {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE} hinzugefügt

Die folgenden APIs wurden hinzugefügt, um alternative Audio zu unterstützen:

**`hasAlternateAudio`**

Wenn das angegebene Medium über eine andere Audiospur als die Standardspur verfügt, gibt diese boolesche Funktion `true` zurück. Wenn keine alternative Audiospur vorhanden ist, gibt die Funktion `false` zurück.

```java
boolean hasAlternateAudio();
```

**`getAudioTracks`**

Diese Funktion gibt die Liste aller aktuell verfügbaren Audiospuren in einem angegebenen Medium zurück.

```java
List<AudioTrack> getAudioTracks();
```

**`getSelectedAudioTrack`**

Diese Funktion gibt die derzeit ausgewählte alternative Audiospur und Eigenschaften wie Sprache zurück. Die automatische Auswahl der Spur kann ebenfalls extrahiert werden.

```java
AudioTrack getSelectedAudioTrack();
```

**`selectAudioTrack`**

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
