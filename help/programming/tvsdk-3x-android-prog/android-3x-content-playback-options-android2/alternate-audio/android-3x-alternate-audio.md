---
description: Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für einen Videotrack wechseln. Benutzer können beim Abspielen des Videos ihren bevorzugten Sprachtrack auswählen.
title: Alternativaudio
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Übersicht {#alternate-audio-overview}

Mit alternativem Audio können Sie zwischen verfügbaren Audiospuren für einen Videotrack wechseln. Benutzer können beim Abspielen des Videos ihren bevorzugten Sprachtrack auswählen.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Wenn TVSDK die `MediaPlayerItem` -Instanz für das aktuelle Video erstellt sie eine `AudioTrack` -Element für jeden verfügbaren Audio-Track. Das Element enthält eine `name` -Eigenschaft, die eine Zeichenfolge ist, die normalerweise eine benutzererkennbare Beschreibung der Sprache dieses Trackings enthält. Das Element enthält auch Informationen darüber, ob diese Verfolgung standardmäßig verwendet werden soll. Wenn es Zeit ist, das Video abzuspielen, können Sie nach einer Liste der verfügbaren Audiospuren fragen, optional zulassen, dass der Benutzer einen Track auswählt und das Video mit dem ausgewählten Track abspielt.

>[!TIP]
>
>Obwohl selten, wenn ein zusätzlicher Audio-Track verfügbar wird, nachdem TVSDK die `MediaPlayerItem`, gibt TVSDK eine `MediaPlayerItem.AUDIO_TRACK_UPDATED` -Ereignis.

## APIs hinzugefügt {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Die folgenden APIs wurden hinzugefügt, um alternative Audio zu unterstützen:

**`hasAlternateAudio`**

Wenn das angegebene Medium über eine andere Audiospur als die Standardspur verfügt, gibt diese boolesche Funktion `true`. Wenn kein alternativer Audio-Track vorhanden ist, gibt die Funktion `false`.

```java
boolean hasAlternateAudio();
```

**`getAudioTracks`**

Diese Funktion gibt eine Liste aller derzeit verfügbaren Audiospuren in einem angegebenen Medium zurück.

```java
List<AudioTrack> getAudioTracks();
```

**`getSelectedAudioTrack`**

Diese Funktion gibt die derzeit ausgewählte alternative Audiospur und Eigenschaften wie Sprache zurück. Auch die automatische Auswahl von Track kann extrahiert werden.

```java
AudioTrack getSelectedAudioTrack();
```

**`selectAudioTrack`**

Diese Funktion wählt einen alternativen Audiotrack zur Wiedergabe aus.

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
